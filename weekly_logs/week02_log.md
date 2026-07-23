# Week 02 Log — Data Ingestion & Pipeline Setup

**Week:** 2  
**Date range:** [Add dates]  
**Team:** Team 19  
**Project:** ClaimIQ: Insurance Risk Analytics

---

## 1. Sprint Goal

The goal of this sprint was to understand the insurance claims dataset, set up the data engineering pipeline, and perform the initial data ingestion process. We focused on cleaning the raw data, validating its quality, and preparing it for further transformation using the Medallion Architecture.

---

## 2. Work Completed

| Task | Owner | Status | Evidence |
|------|-------|--------|----------|
| Studied insurance claims dataset and business requirements | Team 19 | Done | Documentation |
| Imported raw insurance dataset into Databricks | Team 19 | Done | Databricks Notebook |
| Performed data cleaning (duplicates, missing values, invalid records) | Team 19 | Done | Notebook |
| Designed Bronze, Silver, and Gold data pipeline | Team 19 | Done | Architecture Diagram |
| Created GitHub repository structure | Team 19 | Done | GitHub Repository |
| Planned Power BI dashboard KPIs | Team 19 | In Progress | Dashboard Design |

---

## 3. Key Decisions

- Adopted the **Medallion Architecture (Bronze → Silver → Gold)** to ensure scalable and organized data processing.
- Selected **Databricks** for ETL development and **Power BI** for business intelligence dashboards.

---

## 4. Blockers / Risks

| Blocker | Impact | Help Needed |
|----------|--------|-------------|
| Missing and inconsistent values in the raw dataset | Slowed data transformation | Additional data validation and cleaning |
| Limited understanding of insurance domain terminology | Difficulty defining business KPIs | Guidance from mentors and documentation |

---

## 5. Evidence Added to GitHub

- Added Databricks notebooks for data ingestion.
- Uploaded data cleaning notebook.
- Added Medallion Architecture diagram.
- Updated project README with pipeline overview.
- Uploaded sample insurance dataset.

---

## 6. AI Transparency Note

| Question | Response |
|----------|----------|
| Where AI helped | AI assisted in understanding the insurance domain, Medallion Architecture, ETL workflow, and improving project documentation. |
| What we changed after AI suggestion | Improved the pipeline design, standardized column names, enhanced data cleaning steps, and updated project documentation. |
| What we verified manually | Verified dataset quality, notebook execution, duplicate removal, missing value handling, schema validation, and GitHub commits. |
| What we can explain without AI | Project objectives, ETL pipeline, Medallion Architecture, Databricks workflow, data cleaning process, and dashboard KPIs. |

---

## 7. Next Week Preparation

- Transform Bronze layer data into the Silver layer.
- Apply business rules and data validation.
- Generate Gold layer datasets for analytics.
- Begin Power BI dashboard development.
- Perform data quality testing and documentation updates.
