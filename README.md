# LinkedIn Job Market Trends Analysis

This project implements an end-to-end Python ETL pipeline to analyze job postings, company metrics, and industry trends using the LinkedIn Job Postings dataset.

## Project Structure

```text
SectionA_Team14_JobMarketTrends/
├── notebooks/
│   ├── 02_cleaning.ipynb           # Multi-dataset ETL (Ingestion, Merge, Clean, Transform)
│   └── 03_eda_visualizations.ipynb # Exploratory Analysis & Data Visualization
├── linkedin_jobs_dashboard_ready.csv # Final production-ready dataset
├── DVA_CAPSTONE.ipynb              # Legacy experimental notebook
└── README.md                       # Documentation
```

## ETL Pipeline Details (02_cleaning.ipynb)

The pipeline integrates multiple data sources from Kaggle:
- **Primary Data**: `postings.csv`
- **Company Data**: `companies.csv`, `employee_counts.csv`
- **Industry Data**: `company_industries.csv`, `industries.csv`
- **Skills Data**: `job_skills.csv`, `skills.csv`

### Steps:
1. **Ingestion**: Automated download/caching from Kaggle using `kagglehub`.
2. **Merging**: Deep joins across jobs, companies, industries, and **skills mapping**.
3. **Cleaning**: Deduplication, type casting (Int64, datetime64), and null handling.
4. **Feature Engineering**:
   - `demand_score`: Weighted index of views and applies.
   - `experience_group`: Simplified job levels.
   - `is_remote`: Binary classification.
   - **Skills Integration**: Consolidated skill requirements per job.
5. **Step Logging**: Explicit merge tracking for data lineage.

## Analysis & Insights (03_eda_visualizations.ipynb)

The analysis focuses on:
- **Salary Benchmarks**: Distribution across experience levels.
- **Top Skills**: Most in-demand technical and soft skills.
- **Remote Work**: Accessibility trends.
- **Industry & Company Size**: Demand distribution metrics.

## Getting Started

1. Ensure you have the required libraries: `pandas`, `numpy`, `matplotlib`, `seaborn`, `kagglehub`.
2. Run `notebooks/02_cleaning.ipynb` to generate the enriched dataset.
3. Explore the results in `notebooks/03_eda_visualizations.ipynb`.