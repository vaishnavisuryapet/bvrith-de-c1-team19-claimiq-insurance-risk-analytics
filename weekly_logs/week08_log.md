# Week 08 Log — Power BI Dashboard Preparation

**Week:** 8   
**Team:** 19  
**Project:** ClaimIQ – Insurance Risk Analytics

---

## 1. Sprint Goal

Prepare the validated Gold-layer outputs for Power BI and develop the initial ClaimIQ dashboard using only approved Gold-layer data. Ensure that the Power BI model, KPIs, visuals, filters, and dashboard values remain traceable to the validated Gold tables.

---

## 2. Work Completed

| **Task** | **Owner** | **Status** | **Evidence** |
|---|---|---|---|
| Reviewed finalized Gold tables | [V.Abhigna] | Done | Databricks screenshots |
| Validated Gold table data and KPIs | [V.Abhigna] | Done | Gold validation results |
| Prepared Gold data for Power BI | [V.Abhigna] | Done | Power BI export notebook |
| Connected approved Gold tables to Power BI | [V.Abhigna] | Done | Power BI model screenshot |
| Created Gold-only Power BI semantic model | [V.Abhigna] | Done | Power BI model |
| Created KPI cards for claims metrics | [S.Vaishnavi] | Done | Power BI dashboard |
| Created claim/product analysis visuals | [S.Vaishnavi] | Done | Power BI dashboard |
| Created requested vs approved amount visuals | [S.Vaishnavi] | Done | Power BI dashboard |
| Created monthly claims trend visuals | [S.Vaishnavi] | Done | Power BI dashboard |
| Added slicers for interactive filtering | [S.Vaishnavi] | Done | Power BI dashboard |
| Tested slicer interactions | [Gayathri] | Done | Power BI screenshots |
| Reconciled dashboard values with Gold data | [Gayathri] | Done | Databricks/Power BI comparison |
| Updated dashboard README and Week 08 evidence | [Gayathri] | Done | GitHub repository |

---

## 3. Key Decisions

- Power BI uses only the approved Gold-layer outputs.
- The Power BI model contains the four approved Gold summary tables:
  - `gold_claims_product_monthly_summary`
  - `gold_claims_region_risk_monthly`
  - `gold_claims_sla_performance_monthly`
  - `gold_claims_payment_monthly`
- The Gold tables were kept independent because they represent different business grains and no safe relationship was required between them.
- No raw, Bronze, Silver Candidate, Trusted Silver, or Quarantine tables were connected to Power BI.
- KPI cards were used for important validated claims and payment metrics.
- Product, category, monthly trend, requested-versus-approved, payment, risk-band, settlement, and SLA visuals were created using supported Gold fields.
- Slicers were added to support interactive dashboard analysis.
- Dashboard values were compared against validated Gold-layer results to maintain consistency with the Databricks pipeline.
- The dashboard was designed as a business-facing claims and insurance risk analytics view rather than a raw-data exploration page.

---

## 4. Blockers / Risks

| **Blocker** | **Impact** | **Help Needed** |
|---|---|---|
| Multiple Gold tables have different business grains | Unsafe relationships could produce incorrect results | Keep Gold tables independent where no safe relationship exists |
| KPI values need to match Databricks Gold results | Incorrect values could affect dashboard reliability | Reconcile important dashboard values with Gold queries |
| Large number of available Gold attributes | Too many fields can make dashboard design difficult | Select business-relevant fields and measures |
| Some Gold tables contain narrower analytical populations | Direct comparison between different Gold tables may be misleading | Document table grain and analytical scope |
| Dashboard slicer interactions require testing | Incorrect filter behavior may affect interpretation | Test slicers and visual interactions |

---

## 5. Evidence Added to GitHub

- Updated `notebooks/06_powerbi_export.ipynb`.
- Added/updated `dashboard/powerbi_dashboard.pbix`.
- Added Power BI dashboard screenshots.
- Added Gold-layer validation evidence.
- Updated `dashboard/README.md`.
- Updated `weekly_logs/week08_log.md`.
- Updated dashboard-related documentation.
- Recorded reconciliation results between Power BI and the validated Gold-layer outputs.

### Key validated Gold-layer values

| **Metric** | **Validated Value** |
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

## 6. AI Transparency Note

| **Question** | **Response** |
|---|---|
| Where AI helped | AI was used to support Power BI visual selection, KPI design, dashboard layout, slicer configuration, SQL interpretation, and reconciliation planning. |
| What we changed after AI suggestion | Suggested dashboard structures and metrics were adapted to the actual ClaimIQ Gold tables, available fields, business requirements, and validated results. |
| What we verified manually | Gold-table values, KPI calculations, claim counts, requested and approved amounts, payment metrics, SLA metrics, Power BI visuals, filters, and dashboard results were manually checked against the Databricks outputs. |
| What we can explain without AI | The team can explain the Bronze → Silver → Gold pipeline, Gold-table purposes and grains, KPI definitions, Power BI model, dashboard visuals, slicers, reconciliation process, and the business meaning of the displayed insurance metrics. |

---

## 7. Next Week Preparation

- Refine the ClaimIQ Power BI dashboard for Week 9.
- Review dashboard visual clarity, layout, labels, and accessibility.
- Test slicer and visual interactions across the dashboard pages.
- Reconcile important filtered dashboard values against the owning Gold tables.
- Document evidence-backed dashboard insights and known limitations.
- Update dashboard README and Week 9 evidence.
- Prepare the refined dashboard for the Week 9 review.
