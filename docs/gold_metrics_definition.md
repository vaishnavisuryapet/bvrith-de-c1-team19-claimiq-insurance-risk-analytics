# Gold Metrics Definition

**Week:** 7
**Project:** ClaimIQ – Insurance Risk Analytics
**Purpose:** Define dashboard-ready Gold tables and KPI formulas for insurance claims, policies, customers, and risk analysis.

---

## 1. Gold Table Catalog

| Gold Table Name       | Grain                     | Source Table(s)                                        | Purpose                                                                              |
| --------------------- | ------------------------- | ------------------------------------------------------ | ------------------------------------------------------------------------------------ |
| `gold_claim_summary`  | One row per claim         | `silver_claims`                                        | Provides cleaned claim-level information for claim analysis and dashboard reporting. |
| `gold_policy_summary` | One row per policy        | `silver_policies`                                      | Provides policy-level information for monitoring policy status and performance.      |
| `gold_customer_risk`  | One row per customer      | `silver_customers`, `silver_claims`, `silver_policies` | Combines customer, claim, and policy information to support customer risk analysis.  |
| `gold_claim_metrics`  | One row per date/category | `silver_claims`                                        | Provides aggregated claim counts and financial metrics for dashboards.               |
| `gold_policy_metrics` | One row per date/category | `silver_policies`                                      | Provides aggregated policy counts and status-based metrics.                          |

---

## 2. KPI Definitions

| KPI Name                     | Formula                                                      | Grain              | Dashboard Page  | Notes                                                          |
| ---------------------------- | ------------------------------------------------------------ | ------------------ | --------------- | -------------------------------------------------------------- |
| Total Claims                 | `COUNT(DISTINCT claim_id)`                                   | Overall / monthly  | Claims Overview | Counts unique insurance claims.                                |
| Total Claim Amount           | `SUM(claim_amount)`                                          | Overall / monthly  | Claims Overview | Total financial value of claims.                               |
| Average Claim Amount         | `SUM(claim_amount) / COUNT(DISTINCT claim_id)`               | Overall / monthly  | Claims Overview | Measures the average value per claim.                          |
| Total Policies               | `COUNT(DISTINCT policy_id)`                                  | Overall / monthly  | Policy Overview | Counts unique insurance policies.                              |
| Active Policies              | `COUNT(DISTINCT policy_id)` where `policy_status = 'Active'` | Overall / monthly  | Policy Overview | Measures currently active policies.                            |
| Total Customers              | `COUNT(DISTINCT customer_id)`                                | Overall            | Customer/Risk   | Number of unique customers.                                    |
| Claims by City               | `COUNT(DISTINCT claim_id)` grouped by `city`                 | City               | Claims Analysis | Used to identify geographic claim patterns.                    |
| Claim Amount by City         | `SUM(claim_amount)` grouped by `city`                        | City               | Claims Analysis | Shows total claim value by location.                           |
| Claims by Policy Type        | `COUNT(DISTINCT claim_id)` grouped by `policy_type`          | Policy type        | Claims Analysis | Compares claims across policy categories.                      |
| Average Claim by Policy Type | `AVG(claim_amount)` grouped by `policy_type`                 | Policy type        | Claims Analysis | Identifies policy categories with higher average claim values. |
| Claim Frequency              | `COUNT(DISTINCT claim_id) / COUNT(DISTINCT policy_id)`       | Overall / category | Risk Analysis   | Indicates the number of claims relative to policies.           |
| Customer Claim Amount        | `SUM(claim_amount)` grouped by `customer_id`                 | Customer           | Risk Analysis   | Used as one input for customer-level risk analysis.            |

---

## 3. Example Gold Transformations

### Gold Claim Metrics

The Gold claim metrics table can contain aggregated information such as:

| Date       | Claim Count | Total Claim Amount | Average Claim Amount |
| ---------- | ----------: | -----------------: | -------------------: |
| 2026-07-01 |     [count] |           [amount] |             [amount] |
| 2026-07-02 |     [count] |           [amount] |             [amount] |
| 2026-07-03 |     [count] |           [amount] |             [amount] |

This table can be used directly for trend visualizations in Power BI.

### Gold Customer Risk

The customer risk table can contain:

| Customer ID | Total Claims | Total Claim Amount | Policy Count | Risk Category     |
| ----------- | -----------: | -----------------: | -----------: | ----------------- |
| [ID]        |      [count] |           [amount] |      [count] | [Low/Medium/High] |

The risk category should be based on the **risk logic defined by the project**, rather than an arbitrary classification.

---

## 4. Validation Checks

Before using Gold tables in Power BI, verify:

* Gold row counts are reasonable compared with the corresponding Silver tables.
* No unexpected null values exist in key dashboard fields such as `claim_id`, `policy_id`, and `customer_id`.
* Duplicate records are not present where the Gold table requires a unique grain.
* Total claim counts match manual calculations from the Silver claims table.
* Total claim amounts match manual aggregation of valid claim records.
* Policy counts and active-policy counts match the Silver policy data.
* Customer, policy, and claim joins do not unexpectedly increase the number of records.
* KPI calculations are consistent across Databricks and Power BI.
* Power BI uses the validated Gold outputs rather than directly accessing raw Bronze data.
* Metric formulas and business definitions are documented so that the team can explain every dashboard KPI.

---

## 5. Gold Layer Design Principle

The Gold layer is designed to provide **business-ready, dashboard-ready datasets** rather than simply copying the Silver tables.

The Gold tables contain aggregated and transformed information required for ClaimIQ's insurance analytics use cases. The main objectives are to make the data easier to consume, improve dashboard performance, maintain consistent KPI definitions, and ensure that business users receive validated metrics.
