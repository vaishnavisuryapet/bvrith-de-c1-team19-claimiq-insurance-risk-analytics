# Week 04 Log — Silver Layer Development & Data Quality Validation

**Week:** 4  
**Date range:** [Add dates]  
**Team:** Team 19  
**Project:** ClaimIQ: Insurance Risk Analytics

---

## 1. Sprint Goal

The goal of this sprint was to transform the cleaned Bronze layer data into the Silver layer by applying business rules, validating data quality, and integrating multiple datasets. The team focused on creating standardized, reliable, and analytics-ready data for reporting.

---

## 2. Work Completed

| Task | Owner | Status | Evidence |
|------|-------|--------|----------|
| Developed Silver layer transformation pipeline | Team 19 | Done | Databricks Notebook |
| Integrated claims, customer, and policy datasets | Team 19 | Done | ETL Notebook |
| Applied business validation rules | Team 19 | Done | SQL Scripts |
| Removed duplicate records and handled missing values | Team 19 | Done | Data Quality Report |
| Standardized column names and data formats | Team 19 | Done | Silver Table |
| Validated transformed dataset | Team 19 | Done | Validation Report |

---

## 3. Key Decisions

- Adopted standardized field names and consistent data types across all Silver tables.
- Applied data quality checks before loading data into the Silver layer to improve reliability for analytics.

---

## 4. Blockers / Risks

| Blocker | Impact | Help Needed |
|----------|--------|-------------|
| Data inconsistencies between source files | Delayed integration process | Additional validation and transformation rules |
| Missing reference values in some records | Reduced completeness of analytics | Manual verification and data enrichment |

---

## 5. Evidence Added to GitHub

- Uploaded Silver layer Databricks notebook.
- Added SQL transformation scripts.
- Uploaded data quality validation report.
- Updated ETL workflow documentation.
- Added screenshots of Silver tables and transformation results.

---

## 6. AI Transparency Note

| Question | Response |
|----------|----------|
| Where AI helped | AI assisted in designing ETL transformations, suggesting data validation rules, SQL queries, and documentation improvements. |
| What we changed after AI suggestion | Improved column standardization, optimized transformation logic, and added additional data quality checks. |
| What we verified manually | Verified transformed records, joins between datasets, data types, validation rules, and Silver layer outputs. |
| What we can explain without AI | The complete ETL process, Silver layer architecture, data cleaning techniques, transformation logic, SQL queries, and validation methods. |

---

## 7. Next Week Preparation

- Build the Gold layer for business analytics.
- Create Power BI dashboards using Gold layer data.
- Generate insurance claim KPIs and business reports.
- Perform end-to-end pipeline testing and optimize ETL performance.
