# Week 04 Log — Silver Layer & Data Quality

**Week:** 4  
**Date range:** [Add your Week 04 dates]  
**Team:** Team 19  
**Project:** ClaimIQ – Insurance Risk Analytics

---

## 1. Sprint Goal

The goal of Week 04 was to transform the Bronze-layer insurance data into a clean and structured Silver layer. We also started implementing data quality checks to identify missing, duplicate, inconsistent, and invalid records before moving the data to the Gold layer.

---

## 2. Work Completed

| Task | Owner | Status | Evidence |
|---|---|---|---|
| Reviewed Bronze-layer insurance datasets | Abhigna Voddati | Done | Databricks Notebook |
| Cleaned and standardized insurance claim data | Suryapeta Vaishnavi | Done | Silver transformation notebook |
| Handled missing and inconsistent values | Gayathri Indukuri | Done | Data cleaning notebook |
| Removed duplicate claim records | Suryapeta Vaishnavi | Done | Databricks Notebook |
| Standardized date and categorical columns | Abhigna Voddati | Done | Silver-layer notebook |
| Created Silver-layer datasets | Team | Done | Silver output files |
| Performed data quality validation | Team | Done | Data Quality notebook |
| Checked invalid claim amounts and policy values | Team | Done | Data Quality results |
| Updated project documentation | Team | Done | GitHub README / Week 04 Log |

---

## 3. Key Decisions

- We decided to use the Bronze layer as the source for all Silver-layer transformations.
- Missing and inconsistent values were handled during the Silver-layer transformation instead of modifying the original Bronze data.
- Duplicate claim records were identified and removed using appropriate claim-related identifiers.
- Date, numerical, and categorical columns were standardized to maintain consistency across datasets.
- Data quality checks were introduced before the data moves to the Gold layer.
- The original raw and Bronze datasets were preserved so that transformations remain traceable and reproducible.

---

## 4. Blockers / Risks

| Blocker | Impact | Help Needed |
|---|---|---|
| Some records contained missing values | May affect analysis and dashboard results | Team review of suitable handling methods |
| Inconsistent values in categorical columns | Can produce incorrect grouping and analysis | Standardization rules were defined |
| Duplicate records in claim data | May affect claim counts and risk calculations | Duplicate detection and removal |
| Different date formats in source data | Can cause issues during analysis | Standardized date format |
| Invalid or unusual numerical values | Can affect risk calculations | Data quality validation rules |

---

## 5. Evidence Added to GitHub

- Updated Week 04 Log.
- Added/updated Silver-layer transformation notebook.
- Added data quality validation notebook.
- Added cleaned Silver-layer datasets.
- Added screenshots of Databricks transformation results.
- Added screenshots/results of data quality checks.
- Updated README with current project pipeline progress.

---

## 6. AI Transparency Note

| Question | Response |
|---|---|
| Where AI helped | AI was used to understand data-cleaning approaches, suggest transformation logic, explain PySpark/Databricks concepts, and help identify possible data quality checks. |
| What we changed after AI suggestion | The team adapted the suggested logic according to the structure and requirements of the ClaimIQ insurance datasets instead of using the suggestions directly. |
| What we verified manually | We manually checked the transformed datasets, duplicate records, missing values, data types, date formats, and validation results. |
| What we can explain without AI | The team can explain the Bronze-to-Silver transformation process, data cleaning, duplicate handling, missing-value handling, standardization, data quality checks, and the purpose of each pipeline layer. |

---

## 7. Next Week Preparation

- Complete and validate the Silver-layer datasets.
- Strengthen data quality rules and validation checks.
- Begin preparing the Gold-layer datasets.
- Define business-level insurance risk metrics.
- Prepare datasets required for Power BI dashboards.
- Continue updating GitHub documentation and project evidence.
