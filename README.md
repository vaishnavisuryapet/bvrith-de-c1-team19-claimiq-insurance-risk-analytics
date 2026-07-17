# ClaimIQ: Insurance Risk Analytics

> **Student Note:** Start with `00_START_HERE.md` and `00_TEMPLATE_INDEX.md`. The placeholder files inside this repository serve as templates for the project.

**Program:** ZENAIZ x BVRIT Hyderabad Data Engineering Internship Program  
**Track:** Data Engineering  
**Duration:** 12 Weeks  
**Team:** 19  
**Students:** Abhigna Voddati, Suryapeta Vaishnavi, Gayathri Indukuri  
**AI Teammate:** Used responsibly for explanation, debugging, documentation support, and code review. All AI-generated content was manually verified before implementation.

---

# 1. Project Summary

- **Domain:** Insurance Risk Analytics
- **Core Engineering Problem:** Insurance companies collect large volumes of policyholder and claim data from multiple sources. This raw data often contains inconsistencies, duplicates, and missing values, making it unsuitable for direct analysis. The project transforms this data into reliable, analytics-ready datasets.
- **Main Pipeline:** Raw Insurance Data → Bronze → Silver → Data Quality → Gold → Power BI Dashboard → Streaming Simulation
- **Final Outcome:** A complete end-to-end data engineering pipeline built using Databricks, producing trusted Gold datasets, interactive Power BI dashboards, streaming claim event simulations, and comprehensive GitHub documentation with weekly evidence.

---

# 2. Tools Used

| Tool | Purpose |
|------|---------|
| Databricks Community Edition | Build Spark SQL and PySpark notebooks for Bronze, Silver, Gold, Data Quality, and Streaming |
| Apache Spark | Large-scale data processing and transformations |
| Python (Pandas & PySpark) | Data cleaning, preprocessing, and feature engineering |
| GitHub | Version control, documentation, sprint logs, and project evidence |
| Power BI Desktop | Dashboard creation and visualization using Gold datasets |
| AI Assistant | Documentation support, debugging, explanation, and code review with manual verification |

---

# 3. Repository Navigation

| Folder / File | Purpose |
|--------------|---------|
| `docs/` | Project documentation, problem charter, data dictionary, references, DQ summary |
| `src/` | Data generation scripts, preprocessing utilities, helper functions |
| `notebooks/` | Databricks notebooks for exploration, Bronze, Silver, Data Quality, Gold, export, and streaming |
| `data_sample/` | Sample insurance datasets for testing |
| `dashboard/` | Power BI dashboard (.pbix) and dashboard documentation |
| `streaming/` | Streaming architecture, JSON schema, streaming simulation notebooks |
| `screenshots/` | Weekly implementation screenshots and evidence |
| `weekly_logs/` | Weekly sprint logs and AI transparency reports |
| `final_submission/` | Final report, presentation, demo script, and contribution document |

---

# 4. 12-Week Execution Map

| Week | Focus | Main Evidence |
|------|-------|---------------|
| 1 | Project planning and GitHub setup | README, Problem Charter, Sprint Log |
| 2 | Insurance dataset design | Data Dictionary, ER Diagram, Sample Dataset |
| 3 | Databricks data exploration | Exploration notebook, schema screenshots |
| 4 | Bronze layer implementation | Bronze notebook, raw data ingestion |
| 5 | Silver layer implementation | Cleaned and standardized datasets |
| 6 | Data Quality validation | DQ notebook, validation report |
| 7 | Gold layer creation | Business metrics and aggregated tables |
| 8 | Power BI dashboard development | Initial dashboard and Gold export |
| 9 | Dashboard enhancement | Final dashboard and business insights |
| 10 | Streaming simulation | Structured Streaming notebook and live updates |
| 11 | Pipeline integration | Complete workflow demonstration |
| 12 | Final project submission | Final report, demo, GitHub repository |

---

# 5. Important Rules

- Power BI dashboards will be built only from Gold datasets.
- The project will use publicly available sample insurance data only.
- Any external references will be documented in `docs/references.md`.
- AI-generated code and documentation will always be manually reviewed and verified.
- Every sprint will include GitHub commits, documentation, and supporting screenshots.
- Large datasets will remain outside GitHub and will be recreated using scripts when necessary.

---

# 6. Final Project Proof

By the end of Week 12, this repository will demonstrate that:

- Source insurance datasets were collected and documented.
- Batch data was processed using Databricks and Apache Spark.
- Bronze tables were created from raw insurance data.
- Silver tables were standardized and cleaned.
- Data Quality rules were implemented and validated.
- Gold tables containing business metrics were generated.
- Interactive Power BI dashboards were built using Gold datasets.
- Insurance claim events were simulated using Structured Streaming.
- Weekly progress, documentation, and evidence were maintained in GitHub.
- Every team member can explain the complete end-to-end data engineering pipeline.
