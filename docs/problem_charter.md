# Problem Charter

**Week:** 1  
**Owner(s):** Team 19  
**Project:** ClaimIQ – Insurance Risk Analytics

---

## 1. Problem Context

The insurance industry processes thousands of policy applications and claim requests every day. Insurance companies need to assess the level of risk associated with each customer and identify claims that may require further investigation.

The project uses insurance-related data such as customer demographics, policy details, claim history, vehicle information, medical records (where applicable), and claim amounts. Since this data comes from multiple sources and may contain missing values, duplicates, and inconsistencies, it must be cleaned and standardized before analysis.

The final dashboard and analytics will help insurance managers, risk analysts, and business executives monitor claim trends, evaluate customer risk, detect anomalies, and support data-driven decision-making.

---

## 2. Engineering Problem

The project must convert raw insurance policy and claims datasets into trusted Bronze, Silver, Data Quality, Gold, and dashboard-ready outputs using Databricks and Power BI. The pipeline should clean, validate, transform, and aggregate data to produce reliable risk analytics and business insights.

---

## 3. Users / Stakeholders

| User / Stakeholder | What they need from the data |
|--------------------|------------------------------|
| Insurance Risk Analyst | Analyze customer risk and identify high-risk policies |
| Claims Manager | Monitor claim approvals, fraud indicators, and claim trends |
| Business Executive | View KPIs, claim costs, and business performance |
| Data Engineer | Build and maintain reliable data pipelines |

---

## 4. Scope Inclusions

The team will build:

- Raw insurance dataset ingestion
- Bronze layer for raw data storage
- Silver layer for cleaned and standardized data
- Data Quality validation checks
- Gold layer containing business metrics
- Power BI dashboard for visualization
- Streaming simulation for incoming claim records
- GitHub repository with weekly documentation and project evidence

---

## 5. Scope Exclusions

The team will **not** build:

- A production-ready insurance application
- Real customer or confidential insurance data
- Online policy purchasing or payment gateway integration
- Mobile application development
- AI-generated work without verification
- Fake datasets, screenshots, or copied project submissions

---

## 6. Success Criteria

By the end of 12 weeks, the project will be successful if:

- The complete data pipeline can be demonstrated from Bronze to Gold.
- Data quality checks are implemented and documented.
- Gold layer provides meaningful insurance risk metrics.
- Power BI dashboard displays interactive business insights.
- Streaming simulation successfully processes new claim records.
- Every team member can explain the architecture and workflow.
- GitHub repository contains weekly sprint logs, documentation, source code, notebooks, dashboards, and the final project submission.
