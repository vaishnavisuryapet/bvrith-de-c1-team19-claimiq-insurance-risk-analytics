# Power BI Dashboard — ClaimIQ Risk Insurance

**Team:** 19 | **Weeks:** 8–9 | **File:** `dashboard/powerbi_dashboard.pbix`  
**Upstream:** `notebooks/06_powerbi_export.ipynb`

---

## 1. Purpose

A three-page, Gold-only Power BI report for claims operations, payment
performance, risk review and SLA performance.

All figures are based on validated ClaimIQ Gold-layer outputs generated from
synthetic educational data.

---

## 2. Gold source register

Power BI reads approved **Gold tables only** from Databricks.

No Raw, Bronze, Silver Candidate, Trusted Silver detail or Quarantine table is
connected to the Power BI business-reporting model.

| **Gold table (= Power BI table name)** | **Grain** | **Used for** |
|---|---|---|
| `gold_claims_product_monthly_summary` | product × submission month | claims volume, requested amount, approved amount, product and category analysis |
| `gold_claims_region_risk_monthly` | region × risk band × submission month | risk-band and region-level claims analysis |
| `gold_claims_sla_performance_monthly` | product × settlement month | settlement performance and SLA compliance |
| `gold_claims_payment_monthly` | payment month × payment method | payment volume, paid amount and payment-method analysis |

The Power BI report contains only these four approved Gold summary tables.

---

## 3. Relationships

The four Gold tables are intentionally kept **independent**.

They represent different business grains and no safe relationship is required
between them.

| **Table** | **Relationship** | **Status** |
|---|---|---|
| `gold_claims_product_monthly_summary` | No relationship to other Gold summaries | Independent |
| `gold_claims_region_risk_monthly` | No relationship to other Gold summaries | Independent |
| `gold_claims_sla_performance_monthly` | No relationship to other Gold summaries | Independent |
| `gold_claims_payment_monthly` | No relationship to other Gold summaries | Independent |

No artificial relationships were added only to make slicers control unrelated
Gold summaries.

Independent Gold tables remain independent.

---

## 4. Page register

| **Page** | **Business question** | **Main visuals** | **Gold sources** |
|---|---|---|---|
| **Claims Operations Overview** | What is happening across the claims portfolio and products? | KPI cards; claims by product; requested vs approved amount; monthly claims trend; claims by category; settled claims; approval rate; category comparison; claims vs settled trend | `gold_claims_product_monthly_summary` |
| **Payment Performance & Risk Analytics** | How are payments distributed and how is paid amount changing? | KPI cards; payments by method; net paid by method; monthly net payment trend; gross vs net amount; monthly reversed amount; claims paid by method | `gold_claims_payment_monthly` |
| **Risk Review & SLA Performance** | What is the risk-band distribution and how is settlement/SLA performance behaving? | risk-scoped requested amount; settled claims; average settlement days; claims by risk band; SLA compliance by product | `gold_claims_region_risk_monthly`, `gold_claims_sla_performance_monthly` |

Each page is organized around a business question rather than forcing one page
per Gold table.

---

## 5. Slicers and interaction

| **Page** | **Slicers** | **Affects** |
|---|---|---|
| Claims Operations Overview | product category, submission month | visuals based on the claims product Gold table |
| Payment Performance & Risk Analytics | payment month, payment method | visuals based on the payment Gold table |
| Risk Review & SLA Performance | product category | relevant SLA visuals backed by the SLA Gold table |

A slicer does not need to change every visual.

Independent Gold summaries remain independent when there is no safe relationship
between their grains.

Slicer interaction was tested during Week 9. The Product Category slicer on the
Risk Review & SLA Performance page was verified against the relevant SLA
visuals.

---

## 6. Measures

The dashboard uses measures and fields whose business meaning is owned by the
approved Gold tables.

| **Metric** | **Owning Gold table** | **Business meaning** |
|---|---|---|
| Total Claims | `gold_claims_product_monthly_summary` | Total claim count |
| Settled Claims | `gold_claims_product_monthly_summary` | Claims with settled status |
| Total Requested Amount | `gold_claims_product_monthly_summary` | Total requested claim amount |
| Total Approved Amount | `gold_claims_product_monthly_summary` | Total approved claim amount |
| Approval Rate | `gold_claims_product_monthly_summary` | Approved-to-requested ratio |
| Total Payments | `gold_claims_payment_monthly` | Total payment count |
| Distinct Claims Paid | `gold_claims_payment_monthly` | Distinct claims represented in payment data |
| Gross Paid Amount | `gold_claims_payment_monthly` | Gross payment amount |
| Net Paid Amount | `gold_claims_payment_monthly` | Net payment amount after reversals |
| Settled Claims | `gold_claims_sla_performance_monthly` | Settled claims used for SLA analysis |
| Average Settlement Days | `gold_claims_sla_performance_monthly` | Average days from submission to settlement |
| SLA Compliance Rate | `gold_claims_sla_performance_monthly` | Share of settled claims meeting SLA target |
| Claims by Risk Band | `gold_claims_region_risk_monthly` | Claims grouped by approved risk band |

Rates are interpreted according to their Gold-layer business definitions and
are not replaced with unsupported calculations.

---

## 7. Refresh

1. Refresh the approved Gold-layer outputs when the underlying validated data
   changes.
2. Open `dashboard/powerbi_dashboard.pbix` in Power BI Desktop.
3. Select **Refresh**.
4. Confirm that the Power BI values still reconcile to the approved Gold
   outputs.
5. Recheck the important KPI and filtered values before final evidence capture.

---

## 8. Reconciliation — Gold values with no slicer applied

The following baseline values were validated against the approved Gold
outputs.

| **KPI** | **Gold value** |
|---|---:|
| Total Claims | 499 |
| Settled Claims | 157 |
| Total Requested Amount | 120,721,170.51 |
| Total Approved Amount | 56,409,955.71 |

### Payment Gold validation

| **KPI** | **Gold value** |
|---|---:|
| Total Payments | 55 |
| Distinct Claims Paid | 49 |
| Gross Paid Amount | 5,519,005.09 |
| Net Paid Amount | 5,519,005.09 |

### SLA Gold validation

| **KPI** | **Gold value** |
|---|---:|
| Settled Claims | 156 |
| Average Settlement Days | 20.232 |
| Within-SLA Claims | 63 |

The region/risk Gold table is a separate scoped summary and should not be
compared directly with the overall 499-claim product summary.

Pass condition:

The Power BI visual or card must show the same value as its owning Gold query
under the same filter state and aggregation.

---

## 9. Evidence

Week 8 evidence includes:

- `screenshots/week08_01_gold_source_register.png`
- `screenshots/week08_02_export_reconciliation.png`
- `screenshots/week08_03_powerbi_model.png`
- `screenshots/week08_04_dashboard_page_01.png`
- `screenshots/week08_06_measure_reconciliation.png`
- `dashboard/powerbi_dashboard.pbix`
- `notebooks/06_powerbi_export.ipynb`
- `weekly_logs/week08_log.md`

Week 9 evidence includes:

- `screenshots/week09_*.png`
- refined Power BI pages
- filter/interaction testing
- filtered reconciliation evidence
- `docs/dashboard_insights.md`
- `weekly_logs/week09_log.md`

The evidence is based on genuine Power BI and Gold validation outputs.

---

## 10. Known limitations

- The current approved Gold model does not provide dedicated dashboard-ready
  fields for provider performance.
- The current approved Gold model does not provide dedicated age-band
  analysis.
- Coverage comparison is not supported by the current approved Gold tables.
- Reserve analysis is not supported by the current approved Gold tables.
- Lifecycle funnel analysis is not supported by the current approved Gold
  tables.
- A live/streaming event feed is not part of the Week 9 batch dashboard.
- `gold_claims_region_risk_monthly` is a scoped summary and contains fewer
  records than the overall product-level claims summary; the two should not be
  treated as equivalent populations.
- Review indicators are presented using neutral language and do not constitute
  fraud, denial or final investigation conclusions.
- Unsupported business questions are not filled by connecting raw, Bronze,
  Silver Candidate or Trusted Silver detail tables to Power BI.

---

## 11. Week 9 refinement

Week 9 refined the existing Week 8 Gold-only PBIX rather than rebuilding the
report.

Completed refinement areas:

- professional page naming
- visual hierarchy and layout
- slicer testing
- interaction testing
- SLA performance analysis
- risk-band analysis
- metric formatting
- Gold reconciliation
- dashboard evidence preparation
- insight and limitation documentation

Final page names:

1. **Claims Operations Overview**
2. **Payment Performance & Risk Analytics**
3. **Risk Review & SLA Performance**

---

## 12. Week 10 boundary

Week 9 remains a **Gold-only batch dashboard**.

Streaming implementation is not part of the Week 9 dashboard.

Week 10 introduces the controlled streaming simulation and the approved
streaming branch separately.

The Week 9 batch dashboard remains intact and reproducible when streaming work
begins.
