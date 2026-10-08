# Week 09 Log — Dashboard Refinement and Validation

**Week:** 9  
**Date range:** [Add dates]  
**Team:** 19  
**Project:** ClaimIQ – Insurance Risk Analytics

---

## 1. Sprint Goal

Refine and validate the ClaimIQ Power BI dashboards using the finalized Gold-layer data. Ensure that KPIs, charts, filters, slicers, and business metrics are accurate, clearly presented, and traceable to the approved Gold-layer outputs.

---

## 2. Work Completed

| **Task** | **Owner** | **Status** | **Evidence** |
|---|---|---|---|
| Reviewed existing Week 8 Power BI dashboard | [V.Abhigna] | Done | Power BI dashboard |
| Validated KPI cards against Gold tables | [V.Abhigna] | Done | Databricks/Power BI comparison |
| Refined Claims Operations Overview page | [V.Abhigna] | Done | Power BI dashboard |
| Refined Payment Performance & Risk Analytics page | [V.Abhigna] | Done | Power BI dashboard |
| Refined Risk Review & SLA Performance page | [V.Abhigna] | Done | Power BI dashboard |
| Added and tested dashboard slicers | [S.Vaishnavi] | Done | Power BI dashboard |
| Tested Product Category filter interactions | [S.Vaishnavi] | Done | Power BI screenshots |
| Reviewed requested vs approved claim amounts | [S.Vaishnavi] | Done | Power BI visuals |
| Reviewed payment and payment-method metrics | [S.Vaishnavi] | Done | Power BI visuals |
| Reviewed SLA and settlement metrics | [S.Vaishnavi] | Done | Power BI visuals |
| Removed unsupported/zero-value review KPI cards | [Gayathri] | Done | Power BI dashboard |
| Removed SLA visual with unreliable slicer interaction | [Gayathri] | Done | Power BI dashboard |
| Documented evidence-backed dashboard insights | [Gayathri] | Done | `docs/dashboard_insights.md` |
| Updated dashboard README | [Gayathri] | Done | `dashboard/README.md` |
| Updated Week 09 project log | [Gayathri] | Done | `weekly_logs/week09_log.md` |

---

## 3. Key Decisions

- Power BI dashboards continue to use only the approved Gold-layer outputs.
- The validated Week 8 Power BI model was refined rather than rebuilt from scratch.
- The four approved Gold tables remain independent because they represent different business grains and no safe relationship is required between them.
- No artificial relationships were added simply to force slicers across unrelated Gold tables.
- KPI cards were retained for validated business metrics such as total claims, settled claims, requested amount, approved amount, payments, and net paid amount.
- Product, payment, risk-band, settlement, and SLA visuals were retained because they are supported by the available Gold-layer data.
- Standalone zero-value review KPI cards were removed so that zero values were not presented as misleading decision indicators.
- The SLA Breaches by Product visual was removed because its interaction with the Product Category slicer was not reliable.
- Risk-review indicators are treated as operational review indicators and are not interpreted as fraud, denial, or other definitive conclusions.
- Unsupported provider, age-band, coverage, reserve, lifecycle, and streaming analysis was not fabricated because the current approved Gold model does not contain the required fields.

---

## 4. Blockers / Risks

| **Blocker** | **Impact** | **Help Needed** |
|---|---|---|
| KPI values need to remain consistent with Gold tables | Incorrect dashboard values may affect the final analysis | Perform reconciliation against Gold outputs |
| Multiple Gold tables have different grains | Incorrect relationships could produce misleading results | Keep independent Gold tables where no safe relationship exists |
| Review indicators contain zero values in the current Gold data | Standalone zero KPIs may be misleading | Present review indicators carefully and avoid unsupported conclusions |
| Some Week 9 business questions require fields not available in the approved Gold model | Provider, age-band, coverage, reserve and lifecycle analysis cannot be supported | Record as data/model limitations rather than adding non-Gold sources |
| Dashboard interactions need testing | Incorrect slicer behavior may affect displayed results | Test filters and retain only reliable interactions |

---

## 5. Evidence Added to GitHub

- Updated Power BI dashboard.
- Updated dashboard README.
- Added `docs/dashboard_insights.md`.
- Updated `weekly_logs/week09_log.md`.
- Added/updated Week 09 dashboard screenshots.
- Added reconciliation evidence for important dashboard values.
- Documented evidence-backed dashboard observations and known limitations.

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
| Where AI helped | AI was used to support Power BI visual selection, KPI review, dashboard layout, slicer testing, SQL interpretation, documentation, and reconciliation planning. |
| What we changed after AI suggestion | AI suggestions were adapted according to the actual ClaimIQ Gold tables, available attributes, dashboard behavior, and project requirements. |
| What we verified manually | KPI values, claim counts, requested and approved amounts, payment metrics, SLA metrics, slicer interactions, and dashboard results were compared with the approved Gold-layer outputs. |
| What we can explain without AI | The team can explain the ClaimIQ data pipeline, Gold-layer tables, KPI definitions, Power BI visuals, slicers, dashboard interactions, reconciliation process, and the business meaning and limitations of the displayed metrics. |

---

## 7. Next Week Preparation

- Begin the Week 10 streaming simulation scope.
- Preserve the validated Week 9 Power BI dashboard as the batch dashboard baseline.
- Review the ClaimIQ Gold-layer metrics and business definitions before integrating future streaming outputs.
- Prepare the project structure required for the Week 10 streaming implementation.
- Continue maintaining traceability between dashboard metrics and validated Gold-layer outputs.
- Do not claim live or streaming functionality as part of the Week 9 dashboard.
