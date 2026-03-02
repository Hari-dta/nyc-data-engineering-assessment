
## Project Overview

In this project, I analyzed the NYC Jobs dataset using PySpark. The goal was to clean and standardize the data, perform feature engineering, and derive meaningful insights through defined KPIs.

I followed a structured data engineering approach — starting with data cleaning, then building derived features, and finally computing business-focused metrics. Visualizations were added for the most relevant insights.

All transformations were performed using PySpark, and matplotlib was used for visualizing aggregated results.

---

## Assumptions

* Salary ranges were represented using the midpoint.
* Hourly salaries were converted to annual using 2080 working hours.
* Daily salaries were converted using 260 working days.
* Records with missing or invalid salary values were excluded.
* Only valid posting dates were considered for time-based analysis.
* The `preferred_skills` column contained comma-separated values.

---

## Data Processing Approach

The dataset was cleaned by:

* Trimming whitespace and standardizing column names.
* Casting salary columns to numeric types.
* Converting posting dates to proper date format.
* Removing duplicate records.

I created additional features such as salary midpoint, annual salary, and posting year.
For skills analysis, I used `split()` and `explode()` to analyze individual skills separately.

---

## KPIs Implemented

The analysis included:

* Top 10 job categories
* Salary distribution by category
* Correlation between education requirement and salary
* Highest salary per agency
* Average salary per agency (last 2 years)
* Highest paying skills

All KPIs were implemented using Spark transformations and aggregations.

---

## Visualization Strategy

Instead of visualizing every KPI, I focused on key business insights:

* Top 10 job categories
* Top 10 highest paid skills
* Top 10 agencies by average salary

Spark handled all heavy computation. Only limited aggregated results were converted to Pandas for visualization to maintain efficiency.

---

## Challenges & Learnings

* Handling null values, especially in posting dates.
* Fixing date format issues that initially caused parsing failures.
* Efficiently transforming multi-valued skill columns using `explode()`.
* Avoiding unnecessary `collect()` operations to maintain scalability.

This project reinforced best practices in Spark transformations, null handling, and writing modular, production-style code.

---

## Deployment Perspective

In a real-world scenario, this pipeline could be scheduled as a batch Spark job, orchestrated using tools like Airflow, and store cleaned outputs in Parquet format for downstream analytics or dashboards.

---

