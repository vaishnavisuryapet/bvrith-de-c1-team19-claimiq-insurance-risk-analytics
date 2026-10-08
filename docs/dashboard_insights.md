# ClaimIQ Dashboard Insights
**Week:** 9


## Purpose

This document records evidence-backed observations from the Week 9 ClaimIQ Power BI dashboard refinement. Each insight is traceable to the owning Gold table and the corresponding dashboard visual.

---

## Insight 1 — Claims and Approved Amount by Product

### Question / Decision
Which products contribute the largest claim volumes and approved amounts?

### Observation
The Claims Operations Overview page shows differences in claim volume and approved amount across products. The product-level visuals allow users to compare claim frequency with the corresponding approved amount.

### Filter / Time Scope
Default dashboard scope using the full available Gold data.

### Visual / Page
- Page: Claims Operations Overview
- Visuals: Claims by Product; Requested vs Approved Amount by Product

### Owning Gold Table
`gold_claims_product_monthly_summary`

### Measure / Field
- `claim_count`
- `total_approved_amount`
- `product_name`

### Evidence
The product-level values are sourced directly from the Gold claims product monthly summary and reconcile to the validated Gold baseline.

### Interpretation
Product-level differences can help operations teams identify products with higher claim activity and compare requested versus approved financial exposure.

### Limitation
The dashboard does not establish that a product is higher risk solely because it has more claims or a higher approved amount. Product mix, exposure and business volume should be considered before making operational decisions.

---

## Insight 2 — Settlement Performance and SLA Compliance

### Question / Decision
Which products show stronger or weaker settlement performance against their SLA targets?

### Observation
The Risk Review & SLA Performance page compares average settlement days and SLA compliance across products. The dashboard provides a direct view of settlement performance relative to the configured product SLA target.

### Filter / Time Scope
Default dashboard scope using the available settlement-period Gold data.

### Visual / Page
- Page: Risk Review & SLA Performance
- Visuals: Average Settlement Days; SLA Compliance by Product

### Owning Gold Table
`gold_claims_sla_performance_monthly`

### Measure / Field
- `avg_days_to_settlement`
- `sla_compliance_rate`
- `sla_target_days`
- `product_name`

### Evidence
The Gold SLA table contains 156 settled claims, with an overall average settlement duration of approximately 20.232 days and 63 claims within SLA.

### Interpretation
Settlement performance can be used to identify products where claims operations may warrant further review of processing timelines and SLA adherence.

### Limitation
The dashboard summarizes settled claims only. It does not by itself explain the operational causes of SLA breaches or establish why a particular product performs differently.

---

## Insight 3 — Payment Activity and Net Paid Amount

### Question / Decision
How does payment activity vary by payment method and over time?

### Observation
The Payment Performance & Risk Analytics page shows payment counts, claims paid and net paid amount by payment method, together with the monthly payment trend.

### Filter / Time Scope
Default dashboard scope using the full available payment Gold data.

### Visual / Page
- Page: Payment Performance & Risk Analytics
- Visuals: Payments by Payment Method; Net Paid Amount by Payment Method; Monthly Net Payment Trend

### Owning Gold Table
`gold_claims_payment_monthly`

### Measure / Field
- `payment_count`
- `distinct_claims_paid`
- `net_paid_amount`
- `payment_method`
- `payment_month`

### Evidence
The validated Gold payment table contains 55 payments covering 49 distinct paid claims, with gross paid amount and net paid amount both equal to 5,519,005.09 because no reversals were recorded in the validated data.

### Interpretation
Payment-method and monthly trends provide an operational view of how claim payments are being processed and the associated paid financial volume.

### Limitation
The available Gold data contains no recorded reversals in the validated period. Payment trends should therefore not be interpreted as evidence that payment risk is absent.

---

## Reconciliation Baseline

The dashboard baseline was reconciled against the approved Gold tables:

| Metric | Gold baseline |
|---|---:|
| Total Claims | 499 |
| Settled Claims | 157 |
| Total Requested Amount | 120,721,170.51 |
| Total Approved Amount | 56,409,955.71 |
| Total Payments | 55 |
| Distinct Claims Paid | 49 |
| Gross Paid Amount | 5,519,005.09 |
| Net Paid Amount | 5,519,005.09 |
| SLA Settled Claims | 156 |
| Average Settlement Days | 20.232 |
| Within SLA | 63 |

---

## Known Analytical Limitations

The current approved Gold model contains four independent summary tables:

- `gold_claims_product_monthly_summary`
- `gold_claims_region_risk_monthly`
- `gold_claims_sla_performance_monthly`
- `gold_claims_payment_monthly`

The approved Gold model does not currently provide sufficient fields for provider-level analysis, age-band analysis, coverage comparison, reserve analysis, lifecycle funnel analysis, or a streaming event feed. These areas are therefore not represented as fabricated dashboard insights.

The region/risk Gold table is also a narrower matched dataset and should not be treated as equivalent to the complete 499-claim product summary.

Risk-review indicators are presented as operational review indicators only. They are not fraud, denial or other definitive conclusions.

---

## Week 10 Boundary

Streaming simulation and live-event functionality are outside the scope of this Week 9 dashboard refinement. Streaming implementation begins in Week 10.
