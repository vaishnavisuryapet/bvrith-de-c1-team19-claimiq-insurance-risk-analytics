# ClaimIQ Power BI Dashboard

## Purpose
This dashboard provides Gold-layer reporting for ClaimIQ insurance claims operations, payment activity, and risk analysis.

## Data Source
Power BI uses only validated Gold-layer outputs.

Gold tables used:

- `gold_claims_product_monthly_summary`
- `gold_claims_region_risk_monthly`
- `gold_claims_sla_performance_monthly`
- `gold_claims_payment_monthly`

No Bronze, Silver Candidate, Trusted Silver detail, or Quarantine tables are used directly in Power BI.

## Power BI Model
The four Gold tables are independent summary tables with different grains. They are intentionally kept independent rather than joined through artificial relationships.

## Dashboard Pages

### Page 1 — Claims & Product Overview
Key metrics:
- Total Claims
- Settled Claims
- Total Requested Amount
- Total Approved Amount

Main analysis:
- Claims by Product
- Requested vs Approved Amount by Product
- Monthly Claims Trend
- Claims by Product Category
- Settled Claims by Product
- Approval Rate by Product
- Requested vs Approved by Category
- Claims vs Settled Claims Trend

Slicers:
- Product Category
- Submission Month

### Page 2 — Payment & Risk Analysis
Key metrics:
- Total Payments
- Distinct Claims Paid
- Gross Paid Amount
- Net Paid Amount

Main analysis:
- Payments by Payment Method
- Net Paid Amount by Payment Method
- Monthly Net Payment Trend
- Gross vs Net Paid Amount
- Monthly Reversed Amount
- Claims Paid by Payment Method

Slicers:
- Payment Month
- Payment Method

## Validation
Selected Power BI values were reconciled against the Gold-layer results.

Claims reconciliation:
- Total Claims: 499
- Settled Claims: 157
- Total Requested Amount: 120,721,170.51
- Total Approved Amount: 56,409,955.71

Payment reconciliation:
- Total Payments: 55
- Distinct Claims Paid: 49
- Gross Paid Amount: 5,519,005.09
- Net Paid Amount: 5,519,005.09
- Reversals: 0

## Refresh
The Power BI report is refreshed from the validated Gold-layer hand-off. The Gold export notebook provides the controlled hand-off used for Power BI reporting.

## Evidence
Week 8 evidence screenshots are stored under:

`screenshots/`

including the Gold source register, export reconciliation, Power BI model, dashboard page, and measure reconciliation.
