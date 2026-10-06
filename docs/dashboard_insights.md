# Dashboard Insights

**Week:** 9
**Purpose:** Explain what the Power BI dashboard shows.

---

## 1. Dashboard Pages

| Page                              | Purpose                                                                | Main Visuals                                             |
| --------------------------------- | ---------------------------------------------------------------------- | -------------------------------------------------------- |
| Page 1: Claims & Product Overview | Shows overall claim performance, product analysis and approval metrics | KPI cards, bar charts, line chart, slicers               |
| Page 2: Payment & Risk Analysis   | Shows payment performance, claims paid and payment method analysis     | KPI cards, bar charts, line charts, donut chart, slicers |

---

## 2. Key Insights

Write 5–8 insights from the dashboard.

1. The dashboard shows **499 total claims** and **157 settled claims**.
2. The total requested claim amount is **120.72M**, while the total approved amount is **56.41M**.
3. The **Vehicle** category has the highest number of claims, while **Personal Protection** has the lowest.
4. The number of claims shows an increasing trend from **2023 to 2025**.
5. The dashboard compares requested and approved amounts across different insurance products.
6. There are **55 total payments** and **49 distinct claims paid**.
7. The total gross paid amount and net paid amount are both approximately **5.52M**.
8. **Electronic Transfer** is the most commonly used payment method.

---

## 3. How the Dashboard Uses Gold Tables

| Dashboard Page            | Gold Table Used                       | Important Fields                                                                                                                      |
| ------------------------- | ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| Claims & Product Overview | `gold_claims_product_monthly_summary` | `claim_count`, `settled_claim_count`, `total_requested_amount`, `total_approved_amount`, `product_category`, `submission_month`       |
| Claims & Product Overview | `gold_claims_sla_performance_monthly` | `within_sla_count`, `sla_breach_count`, `avg_days_to_settlement`, `settlement_month`                                                  |
| Payment & Risk Analysis   | Gold Payment Summary                  | `payment_count`, `distinct_claims_paid`, `gross_paid_amount`, `net_paid_amount`, `reversed_amount`, `payment_method`, `payment_month` |

---

## 4. Power BI Validation

* [x] Dashboard connects to Gold outputs only.
* [x] Filters work correctly.
* [x] KPI totals match Gold table checks.
* [x] Requested and approved amounts were validated.
* [x] Claim and payment trends were checked.
* [x] Screenshots are saved in `screenshots/`.
* [x] Dashboard story is explainable by all students.
