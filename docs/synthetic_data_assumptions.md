# Synthetic Data Assumptions

**Week:** 2  
**Purpose:** Document the assumptions used to generate synthetic insurance claims data for the ClaimIQ: Insurance Risk Analytics project.

---

## 1. Synthetic Data Boundary

This project uses **synthetically generated insurance claims data** for educational and learning purposes only. The dataset does not represent any real insurance company, customer, policyholder, healthcare provider, vehicle owner, or financial institution. Any names, IDs, policy numbers, claim records, or locations are fictional and created solely for demonstrating data engineering concepts.

---

## 2. Domain Assumptions

| Area | Assumption |
|------|------------|
| Geography / Scope | Hyderabad and nearby regions in Telangana, India |
| Time Period | January 2026 to December 2026 |
| Source Systems | Insurance Claims System, Policy Management System, Customer Management System |
| Event Types | Claim Submitted, Claim Verified, Claim Approved, Claim Rejected, Fraud Alert |
| Reference Data | Policy Types, Customer Details, Claim Categories, Regional Branches |

---

## 3. Data Volume Assumptions

| File | Approximate Rows | Reason |
|------|-----------------:|--------|
| `insurance_claims.csv` | 10,000 | Simulates historical insurance claims |
| `policy_details.csv` | 5,000 | Represents active insurance policies |
| `customer_details.csv` | 5,000 | Stores customer demographic information |
| `claim_events.json` | 2,500 | Simulates real-time claim processing events |

---

## 4. Controlled Data Quality Issues

| Issue Type | Approx. Share | Why Include It |
|------------|--------------:|----------------|
| Duplicate Claim IDs | 0.3% | Tests duplicate detection and removal |
| Missing Values | 2% | Tests null handling and data completeness |
| Invalid Policy IDs | 0.8% | Tests referential integrity between claims and policies |
| Negative Claim Amounts | 0.2% | Tests business validation rules |
| Invalid Claim Dates | 0.2% | Tests chronological consistency and date validation |

---

## 5. Manual Verification

Before using the generated dataset, the team verifies that:

- Row counts match the expected dataset size.
- Claim IDs, Customer IDs, and Policy IDs are unique where required.
- Dates fall within the defined project timeline.
- Claim amounts and premium values are realistic and positive.
- Controlled data quality issues exist in small proportions for ETL testing.
- Source files contain sufficient differences to demonstrate data integration and standardization.
- Relationships between claims, customers, and policies are valid after data transformation.
