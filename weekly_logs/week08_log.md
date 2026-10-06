# Week 08 Log — Power BI Dashboard Preparation

**Week:** 8
**Date range:** [Add dates]
**Team:** 19
**Project:** ClaimIQ – Insurance Risk Analytics

---

## 1. Sprint Goal

Prepare the validated Gold-layer outputs for Power BI and begin developing interactive dashboards for insurance claims and risk analysis. Ensure that the exported Gold data is accurate, business-ready, and suitable for dashboard visualization.

---

## 2. Work Completed

| Task                                          | Owner     | Status | Evidence                 |
| --------------------------------------------- | --------- | ------ | ------------------------ |
| Reviewed finalized Gold tables                | [Student] | Done   | Databricks screenshots   |
| Validated Gold table data and KPIs            | [Student] | Done   | Validation notebook      |
| Exported Gold tables for Power BI             | [Student] | Done   | Power BI export notebook |
| Connected Gold data to Power BI               | [Student] | Done   | Power BI screenshot      |
| Created KPI cards for insurance metrics       | [Student] | Done   | Power BI dashboard       |
| Created charts for claims and policy analysis | [Student] | Done   | Power BI dashboard       |
| Added slicers for interactive filtering       | [Student] | Done   | Power BI dashboard       |
| Reviewed dashboard results against Gold data  | [Student] | Done   | Validation screenshots   |

---

## 3. Key Decisions

* Gold-layer tables were selected as the primary data source for Power BI dashboards.
* KPI cards were used to display important insurance metrics such as total claims, total claim amount, and policy-related metrics.
* Charts were selected to show claim trends, claim amounts, and category/product-level comparisons.
* Slicers were added to allow users to filter dashboard results interactively.
* Dashboard calculations were based on validated Gold data to maintain consistency with the Databricks pipeline.
* The dashboards were designed to provide a clear overview of insurance claims and risk-related performance.

---

## 4. Blockers / Risks

| Blocker                                       | Impact                                            | Help Needed                           |
| --------------------------------------------- | ------------------------------------------------- | ------------------------------------- |
| Gold table export/connection issues           | May delay Power BI dashboard development          | Verify export and connection settings |
| Large number of attributes in Gold tables     | Can make dashboard design difficult               | Select only relevant business fields  |
| KPI values need to match Databricks results   | Incorrect values can affect dashboard reliability | Perform manual validation             |
| Inconsistent or missing values in some fields | Can affect charts and filters                     | Review data-quality results           |

---

## 5. Evidence Added to GitHub

* Updated Power BI export notebook.
* Added Gold-table export results.
* Added Power BI dashboard screenshots.
* Updated Week 08 project log.
* Added dashboard-related documentation.
* Updated project README with Power BI integration progress.

---

## 6. AI Transparency Note

| Question                            | Response                                                                                                                                                                                           |
| ----------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Where AI helped                     | AI was used to understand Power BI visualizations, KPI cards, slicers, Gold-table selection, and dashboard design. It was also used to explain Databricks export and transformation steps.         |
| What we changed after AI suggestion | The suggested dashboard structure and metrics were adapted to the actual ClaimIQ Gold tables and insurance analytics requirements.                                                                 |
| What we verified manually           | KPI values, Gold-table data, exported records, Power BI visualizations, filters, and dashboard calculations were manually checked against the Databricks outputs.                                  |
| What we can explain without AI      | The team can explain the Bronze → Silver → Gold pipeline, Gold-table purpose, KPI definitions, Power BI connection, dashboard visuals, slicers, and the business meaning of the insurance metrics. |

---

## 7. Next Week Preparation

* Complete and refine the ClaimIQ Power BI dashboards.
* Validate all dashboard KPIs against the Gold tables.
* Improve dashboard layout and user interaction.
* Document the complete data pipeline and dashboard architecture.
* Prepare the final dashboard screenshots and project evidence.
* Prepare to explain the business impact of the ClaimIQ insurance analytics solution during the review.
