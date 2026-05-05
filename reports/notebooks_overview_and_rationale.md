## Data Cleaning Summary (Notebook: [02_cleaning.ipynb](notebooks/02_cleaning.ipynb))

Purpose
- Produce a single, analysis-ready dataset from the raw Kaggle export and derive a small set of features used by later notebooks and the dashboard.

Input files used
- [postings.csv](Dataset/postings.csv) (jobs/postings table)
- Company files, employee counts, and job-level skill files included in the Kaggle export (merged inside the notebook)

Step-by-step (practical, non-theoretical)
1. Inspect data: ran `head()`, `info()`, `isnull().sum()` and `duplicated().sum()` to locate missingness and duplicates.
2. Remove duplicates: dropped exact duplicate rows from the postings table.
3. Numeric coercion: converted columns like `job_id`, `company_id`, `views`, `min_salary`, `max_salary`, `applies` to numeric using `pd.to_numeric(errors='coerce')` and set nullable integer types (`Int64`) for ID/location codes.
4. Datetime conversion: converted millisecond timestamps (`original_listed_time`, `listed_time`, `expiry`, `closed_time`) to `datetime` with `pd.to_datetime(..., unit='ms', errors='coerce')`.
5. Text cleanup: trimmed whitespace, cast common text columns to string, and replaced empty/invalid strings (`'', 'nan', 'None'`) with `pd.NA`.
6. Missing-value handling (practical rules applied):
	- `remote_allowed`: fill missing with `0` and cast to `int`.
	- `sponsored`: fill missing with `0`.
	- `company_name`: fill missing with `'Unknown'`.
	- `formatted_experience_level`, `posting_domain`, `skills_desc`: fill with simple labels like `'Not Specified'` or `'Not Provided'`.
7. Salary normalization/imputation: created `avg_salary` from `min_salary`/`max_salary`; imputed `normalized_salary` by group median using `experience_group`, `formatted_work_type`, and `location`.
8. Feature creation: added `is_remote` (mapped from `remote_allowed`), `demand_score = views + applies`, `year`, `month`, `month_name`, and `job_active_days = (expiry - listed_time).dt.days`.
9. Experience grouping: mapped `formatted_experience_level` into simplified buckets via a small function to create `experience_group` (Internship, Entry, Associate, Mid, Senior, Director, Executive, Other).
10. Skills merge: joined `job_skills` to postings to build `skills_df` used for skill-frequency counts and exploded skills outputs.
11. Final subset and export: selected dashboard columns into `dashboard_df`, ensured proper types, filled `pay_period` if missing, coerced `normalized_salary` to numeric, and exported to the dashboard CSV.

Feature list produced (key columns)
- `avg_salary`, `normalized_salary` (imputed), `salary_available` (flag)
- `is_remote`, `demand_score`, `views`, `applies`
- `experience_group`, `year`, `month`, `month_name`, `job_active_days`

Outputs
- [Dataset/linkedin_jobs_dashboard_ready.csv](Dataset/linkedin_jobs_dashboard_ready.csv) — dashboard-ready extract.
- [Dataset/linkedin_skills_exploded.csv](Dataset/linkedin_skills_exploded.csv) — exploded skills file produced from `skills_df`.

How to use this file
- Use the dashboard CSV for charts and Tableau; use `linkedin_skills_exploded.csv` for top-skill frequency analyses.
- If you need different imputation or grouping rules, edit the corresponding cell(s) in [02_cleaning.ipynb](notebooks/02_cleaning.ipynb) and re-run.

Notes
- The notebook emphasizes reproducible, simple rules (coerce → fill → derive → export). All transformations are implemented in the notebook cells so they can be re-run end-to-end.

