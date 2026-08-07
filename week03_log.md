# Week 03 Log — Data Exploration & Analytics

**Week:** 3  
**Date range:** [Add dates]  
**Team:** Team 19  
**Project:** ClaimIQ: Insurance Risk Analytics

---

## 1. Sprint Goal

The goal of this sprint was to perform exploratory data analysis on the ClaimIQ datasets using Databricks. We focused on loading the datasets into Spark DataFrames, validating schemas, analyzing data quality, creating SQL views, and performing initial business analysis using Spark SQL.

---

## 2. Work Completed

| Task | Owner | Status | Evidence |
|---|---|---|---|
| Loaded ClaimIQ datasets into Databricks | Team 19 | Done | Databricks Notebook |
| Explored dataset schemas and record counts | Team 19 | Done | Notebook Output |
| Created temporary SQL views for analysis | Team 19 | Done | SQL Notebook |
| Performed exploratory SQL queries on claims and payments data | Team 19 | Done | SQL Results |
| Conducted null value and duplicate record analysis | Team 19 | Done | Notebook Output |
| Exported the completed Week 03 notebook as HTML | Team 19 | Done | HTML Notebook |

---

## 3. Key Decisions

- Used Spark SQL temporary views to simplify analytical queries across multiple datasets.
- Performed schema validation and data quality checks before proceeding with business analysis.

---

## 4. Blockers / Risks

| Blocker | Impact | Help Needed |
|---|---|---|
| Timestamp compatibility issue while reading the `claims.parquet` dataset | Delayed data exploration and notebook execution | Resolved by using a compatible loading approach for the dataset |
| Understanding relationships between multiple insurance datasets | Increased time required for SQL analysis | Additional dataset documentation and mentor guidance |

---

## 5. Evidence Added to GitHub

- Updated Week 03 log documentation.
- Added completed Databricks Week 03 notebook.
- Uploaded exported HTML notebook.
- Added screenshots of successful notebook execution.
- Updated SQL analysis results.

---

## 6. AI Transparency Note

| Question | Response |
|---|---|
| Where AI helped | AI assisted in debugging Databricks errors, resolving dataset loading issues, improving Spark SQL queries, and enhancing notebook documentation. |
| What we changed after AI suggestion | Corrected dataset loading logic, resolved the Parquet timestamp compatibility issue, improved SQL queries, and organized the notebook workflow. |
| What we verified manually | Verified dataset loading, schema validation, SQL query outputs, record counts, and successful notebook execution in Databricks. |
| What we can explain without AI | Dataset loading process, Spark DataFrame operations, SQL analysis, data quality checks, and the overall Databricks workflow. |

---

## 7. Next Week Preparation

- Perform advanced data transformations using Spark.
- Build Silver-layer datasets by applying business rules.
- Prepare Gold-layer datasets for reporting and analytics.
- Begin dashboard development and KPI visualization.
- Validate transformed datasets and document the ETL process.
