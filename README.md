# LinkedIn Job Market Demand, Salary & Competition Intelligence

## Project Overview

This project analyzes LinkedIn job posting data to understand hiring demand, salary patterns, candidate engagement, remote-work trends, and competition across job categories, locations, and experience levels.

The goal is to move beyond simple job-count analysis and build a decision-ready market intelligence system for recruiters, workforce planners, job platforms, and job seekers.

A job category may have a high number of postings but weak candidate attention, while another category may have fewer postings but stronger salary signals, higher engagement, or greater competition. This project combines demand, compensation, geography, remote-work behavior, and hiring efficiency into one end-to-end analytics solution.

---

## Project Title

**LinkedIn Job Market Demand, Salary & Competition Intelligence**

## Sector

**Human Resources Analytics | Recruitment Intelligence | Labour Market Analytics**

## Team

**Section A - Team 14**

Team Members:

- Palak
- Divya Singh
- Arun
- Krishna Pramod Dubale
- Samarth Sangtani
- Sarvesh Kumar

---

## Business Problem

Recruiters, job platforms, and job seekers often rely on raw job posting counts to understand market demand. However, job count alone does not answer important business questions.

A role may have many postings but low candidate engagement. Another role may have fewer postings but higher salary, stronger conversion, or more competition. Similarly, remote jobs may offer better salary opportunities but may also attract more applicants.

This project solves the problem by analyzing LinkedIn job postings through three major lenses:

1. **Demand Intelligence** — where job demand and candidate attention are strongest.
2. **Salary Intelligence** — which roles, experience levels, and work types offer stronger compensation.
3. **Competition Intelligence** — where applicant competition, hiring difficulty, and application efficiency are highest.

---

## Key Business Questions

This project answers the following questions:

- Which job categories have the highest hiring demand?
- Which categories attract the most candidate views and applications?
- Which states show stronger job market activity?
- Do remote jobs have higher salary and competition than on-site jobs?
- Which job categories offer stronger salary opportunities?
- How does salary vary by experience level?
- Which roles are hard to fill?
- Which job postings receive high views but low applications?
- Which categories show stronger application efficiency?
- How can recruiters improve low-demand job listings?

---

## Objectives

- Clean and transform raw LinkedIn job posting data into a reliable Tableau-ready dataset.
- Analyze demand using job counts, views, applications, conversion rate, and demand segments.
- Study salary patterns across job category, experience level, remote status, and salary bracket.
- Evaluate competition using competition score, application efficiency, days active, and hard-to-fill indicators.
- Build executive-ready Tableau dashboards for demand, salary, and competition analysis.
- Generate actionable recommendations for recruiters, job platforms, workforce planners, and job seekers.

---

## Dataset

The project uses the Kaggle **LinkedIn Job Postings** dataset by `arshkon/linkedin-job-postings`.

The raw data was downloaded using KaggleHub and processed using Python.

### Main Data Sources

| Source File | Role in Analysis |
|---|---|
| `postings.csv` | Main job-level table containing job ID, title, location, work type, salary, views, applications, and posting dates |
| `companies.csv` | Adds company names and company-level details |
| `employee_counts.csv` | Adds latest employee count as a company scale indicator |
| `company_industries.csv` | Maps companies to industry categories |
| `job_skills.csv` | Links jobs to required skills for future skill-demand analysis |
| `postings_tableau_ready.csv` | Final cleaned and enriched dashboard-ready dataset |

### Final Analytical Dataset

- **120,484 job-level records**
- **26 analytical columns**
- Includes job demand, salary, geography, experience, work type, conversion, and competition-related fields

---

## Key Fields

| Field | Meaning |
|---|---|
| `job_id` | Unique job posting identifier |
| `company_name` | Company associated with the posting |
| `title` | Job title |
| `job_category` | Grouped role category |
| `formatted_experience_level` | Experience level of the role |
| `formatted_work_type` | Original work type field |
| `remote_label` | Remote or On-Site classification |
| `location` | Job location |
| `state` | Derived state from location |
| `normalized_salary` | Comparable annual salary where available |
| `salary_bracket` | Grouped salary band |
| `pay_period` | Salary pay period |
| `views` | Number of listing views |
| `applies` | Number of applications |
| `conversion_rate` | Application-to-view conversion indicator |
| `days_active` | Number of days the posting remained active |
| `listing_month` | Posting month |
| `listing_year` | Posting year |
| `demand_score` | Combined demand indicator |
| `demand_segment` | Low, Medium, High, or Very High demand group |
| `competition_score` | Application intensity indicator |
| `efficiency_score` | Application speed indicator |

---

## Tools & Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Statistical Analysis
- Tableau
- Jupyter Notebook
- KaggleHub
- GitHub

---

## Project Workflow

```text
Kaggle Dataset
      ↓
Data Ingestion
      ↓
Data Cleaning
      ↓
Feature Engineering
      ↓
Exploratory Data Analysis
      ↓
Statistical Analysis
      ↓
Tableau Dashboard Development
      ↓
Insights & Recommendations

---
Data Cleaning & ETL Pipeline

All primary cleaning and transformation steps were executed in Python.

ETL Steps
Stage	Method Used	Purpose
Data Ingestion	Downloaded Kaggle dataset using KaggleHub and loaded source CSV files with Pandas	Built the raw data foundation
Merging	Joined postings with company metadata, employee counts, industry labels, and skills	Created enriched job-level data
Duplicate Handling	Removed duplicate records	Improved dataset reliability
Type Conversion	Converted numeric fields and parsed date fields	Prepared data for analysis and Tableau
Text Standardization	Trimmed and standardized text columns	Improved consistency in dashboards
Salary Treatment	Filtered salary outliers using 5th to 95th percentile range	Reduced extreme salary noise
Missing Salary Handling	Salary was not blindly imputed	Treated missing salary as a salary transparency signal
Feature Engineering	Created demand, salary, remote, location, and competition fields	Enabled deeper analysis
Export	Saved Tableau-ready CSV files	Prepared final dashboard input
Feature Engineering

The project created several analytical features to make the raw dataset more useful for business decision-making.

Engineered Features
Feature	Purpose
job_category	Groups job titles into broader business categories
remote_label	Classifies roles as Remote or On-Site
state	Extracts state-level geography from job location
normalized_salary	Creates comparable annual salary values
salary_bracket	Groups salary into readable salary bands
conversion_rate	Measures how effectively views convert into applications
days_active	Measures how long a job remained active
demand_score	Measures overall demand strength
demand_segment	Segments jobs into Low, Medium, High, and Very High demand
competition_score	Measures applicant competition intensity
efficiency_score	Measures application speed over active days
hard_to_fill_flag	Identifies postings with weak response relative to active days
KPI Framework
KPI	Computation Logic	Business Meaning
Total Job Postings	Count of job_id	Market supply and coverage
Average Views	Mean views per posting	Listing visibility
Average Applications	Mean applications per posting	Candidate action
Conversion Rate	Applications divided by views	How effectively views convert into applications
Average Salary	Mean normalized salary for disclosed salary rows	Compensation benchmark
Salary Info %	Share of postings with usable salary	Salary transparency
Competition Score	Applications divided by views	Applicant competition intensity
Efficiency Score	Applications divided by active days	Application speed
Hard-to-Fill %	Weak response relative to active days	Hiring friction indicator
Demand Segment	Low, Medium, High, Very High grouping	Prioritization of opportunities
Dashboard 1: Job Market Demand Intelligence
Objective

To identify where job demand, candidate views, applications, conversion, geography, and demand segments are strongest.

Dashboard Components
Total job posting KPI
Average views KPI
Average applications KPI
Average conversion rate KPI
Job distribution by category and work type
Candidate engagement by job category
Hiring activity over time
Job demand by state map
Views vs applications relationship
Job demand segmentation
Key Findings
The dataset contains 120,484 job postings.
Average views per posting are 14.63.
Average applications per posting are 10.54.
Average conversion rate is 17.52%.
Management, Technology, Healthcare, Sales, and Finance & Accounting dominate job posting volume.
Marketing and HR & Recruiting attract strong candidate engagement.
California, Texas, and Florida appear as major job demand centers.
Most postings fall into the low-demand segment.
High-demand jobs are rare, which means only a small share of postings receive strong candidate attention.
The views vs applications chart shows a positive relationship between visibility and applications.
Some high-view jobs still receive low applications, suggesting possible issues with job attractiveness, salary clarity, or role description.
Business Interpretation

The job market has large posting volume, but candidate attention is uneven. Employers cannot rely only on posting more jobs. They need better job titles, clearer descriptions, salary transparency, and improved targeting to convert views into applications.

Dashboard 2: Salary & Compensation Intelligence
Objective

To understand salary levels, salary distribution, experience premium, remote salary patterns, and salary bracket concentration.

Dashboard Components
Average salary KPI
Maximum salary KPI
Salary information percentage KPI
Salary distribution chart
Salary by experience level
Salary by job category
Remote vs on-site salary comparison
Salary bracket distribution
Key Findings
Average salary is approximately 94,742.
Maximum salary is approximately 301,600.
Only 29.12% of postings include usable salary information.
Salary transparency is weak across the market.
Executive and Director roles have the highest salary levels.
Entry-level and Internship roles are at the lower end of the salary range.
Data & Analytics and Technology show strong salary signals.
Remote jobs show a salary premium compared to on-site roles.
Most disclosed salaries are concentrated in lower salary brackets.
High-paying roles exist but are relatively rare.
Business Interpretation

Salary visibility is a major gap in the job market. Since only a limited share of postings disclose usable salary information, candidates may face uncertainty while applying. Employers can improve candidate trust and application quality by increasing salary transparency.

Dashboard 3: Competition & Opportunity Intelligence
Objective

To compare competition intensity, application efficiency, remote-vs-on-site competition, demand-salary positioning, and hiring difficulty by category.

Dashboard Components
Average competition KPI
Hard-to-fill percentage KPI
Average efficiency KPI
Competition by category
Efficiency by category
Remote vs on-site competition
Demand vs salary matrix
Hiring difficulty analysis
Key Findings
Average competition is 6.50%.
Hard-to-fill percentage is 1.79%.
Average efficiency is 32.23%.
Remote jobs show higher competition than on-site jobs.
Technology has high applicant competition.
HR & Recruiting and Technology show strong application efficiency.
Data & Analytics and Technology are high-opportunity categories because of stronger salary positioning.
Marketing shows strong engagement and candidate interest.
High-view but low-application jobs may indicate unclear role requirements, weak salary disclosure, poor employer branding, or location mismatch.
Business Interpretation

Remote jobs create more opportunity but also attract more competition. Recruiters should treat remote hiring separately from on-site hiring by using stronger filters, faster screening, and clearer candidate qualification criteria.

Exploratory Data Analysis

EDA was performed across demand, salary, category, geography, time, remote status, and experience segments.

EDA Findings
Views and applications have a positive relationship.
Job posting volume and candidate engagement are not the same.
Marketing, HR & Recruiting, Data & Analytics, Technology, and Finance & Accounting show strong view intensity.
Broad categories such as Management, Technology, Healthcare, Sales, and Finance & Accounting dominate posting volume.
Major economic states show stronger job demand.
Salary increases clearly with experience level.
Remote roles show both salary premium and higher competition.
Most jobs accumulate applications slowly, while a small number receive faster responses.
Statistical Analysis

Statistical testing was performed to validate whether observed differences were meaningful rather than random dashboard noise.

Tests and Results
Analysis	Result	Interpretation
Remote vs On-Site Salary T-Test	p-value = 2.6097e-196	Remote and on-site salary distributions differ significantly
Salary by Job Category ANOVA	p-value = 0.0	Average salary differs significantly across job categories
Category Salary Mean - Data & Analytics	Approx. 144,383	Data & Analytics is one of the strongest-paying categories
Category Salary Mean - Technology	Approx. 131,120	Technology has strong salary positioning
Category Salary Mean - Management	Approx. 118,108	Management also shows strong compensation
Category Salary Mean - Marketing	Approx. 102,936	Marketing has decent salary with strong engagement
Efficiency Distribution	Mean = 0.3223, Median = 0.069	Most roles receive applications slowly, while a few receive fast response
Demand Segmentation	Low = 117,827, Medium = 2,390, High = 235, Very High = 32	High-demand jobs are rare
Main Insights
The market has scale but moderate engagement.
The dataset contains more than 120,000 job postings, but average views and applications per job are limited.
Most roles compete for limited candidate attention.
Low-demand postings dominate the market.
Employers need to improve job descriptions, salary visibility, and targeting instead of relying only on posting volume.
Marketing and HR & Recruiting attract high candidate engagement.
Data & Analytics and Technology offer stronger salary opportunities.
Salary transparency is weak because only 29.12% of postings disclose usable salary information.
Experience level strongly affects salary.
Executive and Director roles sit far above Entry-level and Internship roles in compensation.
Remote jobs show higher salary and higher competition.
California, Texas, and Florida appear as major demand centers.
High-view low-application jobs may reveal problems with role attractiveness or unclear job details.
HR & Recruiting and Technology show strong efficiency in converting candidate interest into applications.
Technology roles are highly competitive and require stronger candidate differentiation.
High-demand jobs are rare and should be studied as best-practice examples.
Recommendations
Priority	Insight	Recommendation	Expected Impact
1	Salary transparency is low	Increase salary disclosure and salary brackets for priority roles	Higher trust, better-fit applications, reduced screening waste
2	Low-demand postings dominate	Improve job titles, descriptions, skill clarity, and targeting	Higher conversion and better listing ROI
3	Data & Analytics and Technology pay more	Benchmark technical compensation and create premium hiring playbooks	Improved offer competitiveness
4	Remote roles have higher competition	Create separate remote hiring funnels with faster screening and stronger filters	Better recruiter productivity and reduced backlog
5	Marketing and HR drive engagement	Use these categories for rapid hiring campaigns and candidate pool building	Faster pipeline creation
Impact Estimation

The project uses public posting data, so the impact estimates are directional. However, because the dataset contains more than 120,000 postings, even small improvements in conversion or hiring efficiency can create meaningful operational impact.

Potential Impact
Action	Impact Logic	Estimated Value
Improve salary transparency	A small conversion lift across low-demand postings would affect the largest market segment	Better candidate-job fit and lower screening waste
Optimize low-demand listings	A 10% improvement in views or applications would improve listing ROI across thousands of postings	Higher recruiter productivity
Separate remote hiring funnel	Remote roles show higher competition, so separate filtering can reduce manual load	Faster shortlisting
Target high-opportunity categories	Focus pay and branding on Data & Analytics and Technology	Higher acceptance probability for skilled roles
Analyze high-demand postings	Learn what makes certain listings perform better	Better job description and targeting strategy
Limitations
The dataset represents LinkedIn job postings and may not include jobs posted on other platforms.
LinkedIn may overrepresent digital, corporate, and urban roles.
Salary analysis is limited because many postings do not disclose salary.
Views and applications measure engagement, not confirmed hiring outcomes.
Listing-month distribution is concentrated around April, so seasonality conclusions should be interpreted carefully.
Broad job categories can hide role-level variation.
Remote labels may simplify hybrid and flexible work arrangements.
Salary fields may vary in format, pay period, and completeness.
Future Scope
Build predictive models for application probability.
Build a hard-to-fill risk prediction model.
Create salary range prediction using job category, experience, location, and remote status.
Build a skill-demand dashboard using the exploded skills dataset.
Integrate external economic indicators such as unemployment rate, GDP, cost of living, and industry growth.
Add scheduled data refresh for near-real-time dashboards.
Create a candidate-facing recommendation tool using demand, salary, and competition signals.
Add company-level hiring intelligence.
Compare LinkedIn trends with other job platforms.
Repository Structure
SectionA_Team14_JobMarketTrends/
│
├── data/
│   ├── raw/
│   ├── processed/
│   └── postings_tableau_ready.csv
│
├── notebooks/
│   ├── 02_cleaning.ipynb
│   ├── 03_eda_visualizations.ipynb
│   ├── 04_statistical_analysis.ipynb
│   └── 05_final_load_prep.ipynb
│
├── tableau/
│   ├── Dashboard 1.png
│   ├── Dashboard 2.png
│   └── Dashboard 3.png
│
├── report/
│   └── project_report.pdf
│
└── README.md
Dashboard Links
Job Market Demand Intelligence

View Dashboard 1 on Tableau Public

Salary & Compensation Intelligence

View Dashboard 2 on Tableau Public

Competition & Opportunity Intelligence

View Dashboard 3 on Tableau Public

How to Read the Dashboards
Dashboard 1

Use this dashboard to understand overall job demand, category-level demand, geographic concentration, and candidate engagement.

Best for answering:

Which categories have the most job postings?
Which categories attract the most views?
Which states show stronger demand?
Are views converting into applications?
How many jobs fall into low, medium, high, and very high demand groups?
Dashboard 2

Use this dashboard to understand compensation patterns.

Best for answering:

Which categories pay more?
How does salary change by experience level?
Are remote jobs paid differently?
What percentage of jobs disclose salary?
Which salary brackets are most common?
Dashboard 3

Use this dashboard to understand competition and opportunity.

Best for answering:

Which categories are most competitive?
Which roles receive applications fastest?
Are remote jobs more competitive?
Which categories combine high demand and high salary?
Which roles may be hard to fill?
Project Notebooks
Notebook	Purpose
02_cleaning.ipynb	Data ingestion, cleaning, merging, and ETL pipeline
03_eda_visualizations.ipynb	Exploratory data analysis and visual exploration
04_statistical_analysis.ipynb	Statistical testing, salary comparison, efficiency analysis, and segmentation
05_final_load_prep.ipynb	Final Tableau-ready dataset preparation
Skills Demonstrated
Data cleaning and preprocessing
Data merging from multiple source files
Feature engineering
Exploratory data analysis
Statistical hypothesis testing
KPI design
Dashboard planning
Tableau storytelling
Business problem framing
Market intelligence analysis
Insight generation
Recommendation building
GitHub project documentation
Interview-Ready Summary

This project analyzes more than 120,000 LinkedIn job postings to understand hiring demand, salary patterns, and applicant competition. I cleaned and transformed raw Kaggle data using Python, engineered business-focused metrics such as conversion rate, demand segment, competition score, efficiency score, and salary transparency, and then built Tableau dashboards for demand, salary, and competition intelligence.

The key insight is that job volume and candidate engagement are not the same. Most postings fall into low-demand segments, while only a small number attract strong candidate attention. Salary transparency is also limited, with only 29.12% of postings providing usable salary data. Data & Analytics and Technology show strong salary opportunities, while Marketing and HR & Recruiting attract high engagement. Remote jobs offer higher salary potential but also face stronger competition.

The project helps recruiters improve job listing quality, compensation strategy, remote hiring funnels, and candidate targeting.

Conclusion

This project converts a large LinkedIn job posting dataset into a practical market intelligence system for recruitment and career decision-making.

The strongest conclusion is that the job market is uneven. Most postings receive limited attention, salary transparency is weak, technical and analytical roles show stronger compensation, and remote roles combine higher opportunity with higher competition.

By combining Python-based ETL, statistical analysis, and Tableau dashboards, this project provides a complete analytics solution that supports better decisions around hiring strategy, salary benchmarking, candidate targeting, and job market positioning.
