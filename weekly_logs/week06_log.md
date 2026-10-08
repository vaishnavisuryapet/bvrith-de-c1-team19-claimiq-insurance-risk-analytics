# Week 06 Log — ClaimIQ

**Week:** 6  
**Team:** Team 19  
**Project:** P19 ClaimIQ

---

## 1. Sprint Goal

Implement DQ01–DQ08 data quality rules for the ClaimIQ Candidate tables. Route valid records to Trusted Silver and failed records to Quarantine while maintaining record-level traceability, failure reasons, severity information, and reconciliation between Candidate, Trusted Silver, and Quarantine.

---

## 2. Work Completed

| **Task** | **Owner** | **Status** | **Evidence** |
|---|---|---|---|
| Implemented DQ01–DQ08 data quality rules | V.Abhigna | Done | `src/data_quality_rules.py` |
| Executed DQ checks on Candidate tables | V.Abhigna | Done | `notebooks/04_data_quality_checks.ipynb` |
| Reviewed DQ rule results and failure reasons | V.Abhigna | Done | DQ validation output |
| Routed valid records to Trusted Silver | S.Vaishnavi | Done | Trusted Silver tables |
| Routed failed records to Quarantine | S.Vaishnavi | Done | `quarantine_claim_records` |
| Preserved failed rule IDs, reasons and severity | S.Vaishnavi | Done | Quarantine table |
| Reviewed Quarantine records and lineage information | S.Vaishnavi | Done | Quarantine validation |
| Created DQ summary by entity, batch, rule and severity | Gayathri | Done | `docs/data_quality_summary.md` |
| Reconciled Candidate = Trusted + Quarantine | Gayathri | Done | Reconciliation output |
| Validated physical-grain row counts | Gayathri | Done | DQ reconciliation evidence |
| Performed controlled rework and replay validation | Gayathri | Done | Rework validation evidence |
| Updated Week 06 documentation and repository evidence | V.Abhigna | Done | GitHub repository |

---

## 3. Key Decisions

- DQ01–DQ08 were implemented as named and reusable data-quality rules with defined severity and reason information.
- Failed records were retained in `quarantine_claim_records` instead of being deleted.
- Records that passed the required data-quality checks were promoted to Trusted Silver.
- Original business columns and lineage information were preserved for failed records.
- Failed rule IDs, failure reasons, and severity were retained to support investigation and controlled rework.
- Candidate physical rows were reconciled against Trusted Silver and Quarantine records.
- Reworked records were required to pass through the Candidate and DQ flow again before promotion.
- Direct insertion of corrected records into Trusted Silver was avoided so that the DQ and lineage process remained traceable.

---

## 4. Blockers / Risks

| **Blocker** | **Impact** | **Help Needed** |
|---|---|---|
| Some records may fail multiple DQ rules | Multiple failure reasons must be retained correctly | Validate rule-level failure output |
| Incorrect routing may cause reconciliation variance | Candidate count may not equal Trusted + Quarantine | Run physical-grain reconciliation |
| Failed records require clear reason and severity information | Missing failure metadata can make rework difficult | Validate quarantine metadata |
| Reworked records must pass through the complete DQ flow | Direct promotion could bypass validation | Re-run Candidate and DQ checks |
| Multiple entities require consistent DQ handling | Inconsistent rules could affect downstream Gold metrics | Review DQ execution across Candidate tables |

---

## 5. Evidence Added to GitHub

- `notebooks/04_data_quality_checks.ipynb`
- `src/data_quality_rules.py`
- `docs/data_quality_summary.md`
- `weekly_logs/week06_log.md`
- DQ01–DQ08 validation output
- Trusted Silver routing evidence
- Quarantine routing evidence
- Candidate vs Trusted + Quarantine reconciliation evidence
- Controlled rework and replay validation evidence

---

## 6. AI Transparency Note

| **Question** | **Response** |
|---|---|
| Where AI helped | AI helped with understanding and structuring DQ01–DQ08 rules, quarantine routing, reconciliation checks, controlled rework, and technical documentation. |
| What we changed after AI suggestion | The suggested implementation was adapted to the actual ClaimIQ Candidate tables, columns, data-quality requirements, and project architecture. |
| What we verified manually | DQ execution, rule IDs, failure reasons, severity, Trusted Silver and Quarantine routing, row counts, reconciliation results, and rework validation were manually checked. |
| What we can explain without AI | The team can explain the Candidate → DQ01–DQ08 → Trusted Silver/Quarantine flow, record-level traceability, reconciliation process, quarantine handling, and controlled rework process. |

---

## 7. Next Week Preparation

- Validate the final Trusted Silver tables.
- Review Quarantine records and controlled rework results.
- Confirm that downstream Trusted Silver data is suitable for Gold-layer processing.
- Prepare Trusted Silver data for Week 07 Gold facts, dimensions, summaries, and KPI aggregations.
- Maintain complete lineage from Candidate through DQ and Trusted/Quarantine outcomes.
- Prepare validation evidence for the Week 07 Gold-layer development.
