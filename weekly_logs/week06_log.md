# Week 06 Log — ClaimIQ

**Week:** 6  
**Date range:** [Add dates]  
**Team:** Team 19  
**Project:** P19 ClaimIQ

---

## 1. Sprint Goal

Implement DQ01–DQ08 data quality rules for the ClaimIQ Candidate tables.  
Route valid records to Trusted Silver and failed records to Quarantine while maintaining complete record-level traceability and reconciliation.

---

## 2. Work Completed

| Task | Owner | Status | Evidence |
|---|---|---|---|
| Implement DQ01–DQ08 data quality rules | [Student A] | Done | `src/data_quality_rules.py` |
| Execute DQ checks on Candidate tables | [Student A] | Done | `notebooks/04_data_quality_checks.ipynb` |
| Route valid records to Trusted Silver | [Student A] | Done | Trusted Silver tables |
| Route failed records to Quarantine | [Student B] | Done | `quarantine_claim_records` |
| Preserve failed rule IDs, reasons and severity | [Student B] | Done | Quarantine table |
| Create DQ summary by entity, batch, rule and severity | [Student C] | Done | `docs/data_quality_summary.md` |
| Reconcile Candidate = Trusted + Quarantine | [Student C] | Done | Validation output |
| Perform controlled rework and replay | [Student B] | In progress | Rework validation |

---

## 3. Key Decisions

- DQ01–DQ08 are represented as named reusable rules with severity and reason text.
- Failed records are retained in `quarantine_claim_records` instead of being deleted.
- Accepted records are promoted to Trusted Silver.
- Original business columns and lineage information are preserved for failed records.
- Candidate physical rows are reconciled against Trusted and Quarantine rows.
- Corrected quarantined records are replayed through Candidate and DQ checks before promotion.

---

## 4. Blockers / Risks

| Blocker | Impact | Help Needed |
|---|---|---|
| Some records may fail multiple DQ rules | Multiple failure reasons must be retained correctly | Validate rule-level failure output |
| Incorrect routing may cause reconciliation variance | Candidate count may not equal Trusted + Quarantine | Run physical-grain reconciliation |
| Reworked records must pass through the complete DQ flow | Direct insertion into Trusted is not allowed | Re-run Candidate and DQ checks |

---

## 5. Evidence Added to GitHub

- `notebooks/04_data_quality_checks.ipynb`
- `src/data_quality_rules.py`
- `docs/data_quality_summary.md`
- `weekly_logs/week06_log.md`
- DQ validation output
- Candidate vs Trusted + Quarantine reconciliation evidence
- Controlled rework validation evidence

---

## 6. AI Transparency Note

| Question | Response |
|---|---|
| Where AI helped | AI helped with structuring DQ01–DQ08 rules, quarantine routing, reconciliation checks and documentation. |
| What we changed after AI suggestion | We adapted the suggested implementation to the actual ClaimIQ Candidate tables, columns and project requirements. |
| What we verified manually | We verified DQ execution, failure reasons, severity, Trusted/Quarantine routing, row counts and reconciliation results manually. |
| What we can explain without AI | We can explain the Candidate → DQ01–DQ08 → Trusted/Quarantine flow, reconciliation process and controlled rework process. |

---

## 7. Next Week Preparation

- Validate the final Trusted Silver tables.
- Review Quarantine and rework results.
- Prepare Trusted data for Week 07 Gold facts, dimensions and KPI aggregations.
