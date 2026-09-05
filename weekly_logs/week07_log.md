# Week 07 Log — Gold Layer & Analytics Preparation

**Week:** 7
**Date range:** [Add dates]
**Team:** 19
**Project:** ClaimIQ – Insurance Risk Analytics

---

## 1. Sprint Goal

Finalize and validate the Gold-layer tables using the cleaned Silver data. Prepare business-ready datasets for Power BI and ensure that the generated metrics are accurate, consistent, and suitable for insurance risk analysis.

---

## 2. Work Completed

| Task                                       | Owner     | Status             | Evidence                         |
| ------------------------------------------ | --------- | ------------------ | -------------------------------- |
| Reviewed Silver-layer data quality results | [Student] | Done               | Databricks notebook / screenshot |
| Created business-ready Gold tables         | [Student] | Done               | Gold tables in Databricks        |
| Created claim and policy summary metrics   | [Student] | Done               | Databricks notebook              |
| Validated Gold-table records and metrics   | [Student] | Done               | Validation queries / screenshots |
| Prepared Gold data for Power BI            | [Student] | Done / In progress | Power BI dataset / screenshot    |
| Reviewed insurance risk-related metrics    | [Student] | In progress        | Analysis notebook                |
| Updated project documentation              | [Student] | Done               | GitHub repository                |

---

## 3. Key Decisions

* Gold tables were designed around business and analytics requirements rather than simply copying the Silver tables.
* High-severity data-quality failures were excluded or flagged before calculating important Gold metrics.
* Claim, policy, customer, and risk-related metrics were validated against the Silver-layer data.
* Gold tables were structured to support Power BI dashboards and easier business analysis.
* Existing Bronze and Silver layers were retained to maintain data lineage and allow the transformations to be traced back to the source.

---

## 4. Blockers / Risks

| Blocker                                                     | Impact                                                   | Help Needed                           |
| ----------------------------------------------------------- | -------------------------------------------------------- | ------------------------------------- |
| Some records contained missing or invalid values            | May affect Gold-level metrics                            | Review data-quality handling          |
| Inconsistent values between related datasets                | Can affect joins between customers, policies, and claims | Validate reference keys               |
| Differences between calculated metrics and expected results | May affect Power BI dashboard accuracy                   | Perform additional validation         |
| Power BI connection/synchronization issues                  | Delays dashboard development                             | Review Databricks/Power BI connection |

---

## 5. Evidence Added to GitHub

* Gold-layer creation notebook updated.
* Gold table transformation queries added.
* Data-quality validation results documented.
* Power BI dashboard screenshots added.
* Week 07 log updated.
* Project README updated with the latest pipeline progress.
* Relevant Databricks notebook screenshots added.

---

## 6. AI Transparency Note

| Question                            | Response                                                                                                                                                                                   |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Where AI helped                     | AI was used to understand data-engineering concepts, suggest transformation approaches, explain Databricks/Spark operations, and assist with debugging SQL/PySpark code.                   |
| What we changed after AI suggestion | The team adapted AI suggestions to match the ClaimIQ dataset, project requirements, table structure, and existing pipeline.                                                                |
| What we verified manually           | Gold-table records, row counts, joins, aggregations, data-quality results, and important insurance metrics were manually checked against the source/Silver data.                           |
| What we can explain without AI      | The team can explain the Bronze–Silver–Gold architecture, data-cleaning process, Gold-table transformations, data-quality checks, business metrics, and the purpose of the Power BI layer. |

---

## 7. Next Week Preparation

* Complete validation of all Gold tables.
* Finalize Power BI dashboards and visualizations.
* Verify important insurance risk and claim metrics.
* Document the complete Bronze → Silver → Gold pipeline.
* Review data lineage and data-quality handling.
* Prepare screenshots and evidence for the next sprint review.
* Identify any remaining pipeline or dashboard issues before final integration.
