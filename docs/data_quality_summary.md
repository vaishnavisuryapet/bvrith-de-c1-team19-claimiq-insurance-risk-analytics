# Data Quality Summary

**Week:** 6
**Project:** ClaimIQ – Insurance Risk Analytics
**Purpose:** Summarize the data quality rules applied to the insurance datasets, identify failed records, and assess their impact on downstream analytics and Gold metrics.

---

## 1. Quality Rule Results

| Rule ID | Rule Name                | Severity | Passed Count | Failed Count | Business Impact                                                                                 |
| ------- | ------------------------ | -------- | -----------: | -----------: | ----------------------------------------------------------------------------------------------- |
| DQ-01   | Required ID not null     | High     |      [count] |      [count] | Records without a valid customer, policy, or claim ID cannot be reliably identified or tracked. |
| DQ-02   | Duplicate key check      | High     |      [count] |      [count] | Duplicate records can cause incorrect claim counts, policy counts, and financial metrics.       |
| DQ-03   | Valid reference key      | Medium   |      [count] |      [count] | Invalid customer or policy references can cause incorrect joins and incomplete analytics.       |
| DQ-04   | Valid timestamp order    | Medium   |      [count] |      [count] | Incorrect event dates can affect claim processing time and other time-based metrics.            |
| DQ-05   | Valid claim amount       | High     |      [count] |      [count] | Negative, null, or invalid claim amounts can distort financial and risk calculations.           |
| DQ-06   | Valid policy status      | Medium   |      [count] |      [count] | Invalid policy statuses can lead to incorrect active, expired, or cancelled policy metrics.     |
| DQ-07   | Valid categorical values | Low      |      [count] |      [count] | Inconsistent categories can create incorrect grouping in dashboards and reports.                |

---

## 2. Failed Record Examples

| Rule ID | Sample Record ID | Failure Reason                                                                | Action / Handling                                                                    |
| ------- | ---------------- | ----------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| DQ-01   | `[customer_id]`  | Customer ID is null or missing.                                               | Flagged for review and excluded from customer-level metrics.                         |
| DQ-02   | `[claim_id]`     | Same claim ID occurs more than once.                                          | Duplicate record identified and removed/flagged according to the deduplication rule. |
| DQ-03   | `[policy_id]`    | Claim refers to a policy ID that does not exist in the policy dataset.        | Record flagged and excluded from dependent joins.                                    |
| DQ-04   | `[claim_id]`     | Claim date occurs before the associated policy start date.                    | Record flagged for validation.                                                       |
| DQ-05   | `[claim_id]`     | Claim amount is null, negative, or outside the expected range.                | Record flagged and excluded from financial aggregations until validated.             |
| DQ-06   | `[policy_id]`    | Policy status contains an unexpected value.                                   | Value standardized where possible; otherwise record flagged.                         |
| DQ-07   | `[record_id]`    | Category contains inconsistent values such as different spellings or formats. | Values standardized during Silver transformation.                                    |

---

## 3. What Should Block Gold Metrics?

The following rules should block or strongly flag Gold table generation because they can directly affect important insurance metrics:

* **DQ-01 – Required ID not null:** Missing identifiers prevent reliable record tracking and joining.
* **DQ-02 – Duplicate key check:** Duplicate claims or policies can significantly inflate business metrics.
* **DQ-03 – Valid reference key:** Invalid relationships can produce incomplete or incorrect joins between customers, policies, and claims.
* **DQ-05 – Valid claim amount:** Invalid financial values can directly distort total claim amount, average claim amount, and risk calculations.

Medium- and low-severity failures can generally be **flagged for review** while allowing the pipeline to continue, depending on the percentage of affected records.

---

## 4. Quality Summary

The ClaimIQ dataset was evaluated using multiple data quality rules covering completeness, uniqueness, referential integrity, timestamp consistency, financial values, and categorical consistency. High-severity checks focused mainly on missing identifiers, duplicate records, invalid references, and invalid claim amounts because these issues can directly affect insurance analytics. Failed records were identified and either corrected during Silver-layer processing, flagged for review, or excluded from downstream calculations where necessary. Data quality checks help ensure that Gold tables contain reliable information for Power BI dashboards and risk analysis. Particular attention should be given to duplicate claims, invalid claim amounts, and broken customer-policy-claim relationships. The mentor should review the handling of high-severity failures and confirm that the chosen thresholds and exclusion rules are appropriate for the business requirements.
