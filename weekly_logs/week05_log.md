# Week 05 - ClaimIQ Silver Layer Transformation

from pyspark.sql.functions import *
from pyspark.sql.types import *

# --------------------------------------------------
# 1. Read Bronze Tables
# --------------------------------------------------

claims_df = spark.table("bronze_claimiq_claims")
policies_df = spark.table("bronze_claimiq_policies")
policyholders_df = spark.table("bronze_claimiq_policyholders")
products_df = spark.table("bronze_claimiq_products")
providers_df = spark.table("bronze_claimiq_providers")
claim_payments_df = spark.table("bronze_claimiq_claim_payments")


# --------------------------------------------------
# 2. Silver Claims
# --------------------------------------------------

silver_claims = (
    claims_df
    .withColumn("claim_id", trim(col("claim_id")))
    .withColumn("policy_id", trim(col("policy_id")))
    .withColumn("policyholder_id", trim(col("policyholder_id")))
    .withColumn("product_id", trim(col("product_id")))
    .withColumn("provider_id", trim(col("provider_id")))
    .withColumn("claim_type", trim(col("claim_type")))
    .withColumn("loss_category", trim(col("loss_category")))
    .withColumn("claim_status", trim(col("claim_status")))
    .withColumn("risk_band", trim(col("risk_band")))
    .withColumn("currency_code", trim(col("currency_code")))
    .withColumn("loss_date", to_date(col("loss_date")))
    .withColumn("submission_timestamp", to_timestamp(col("submission_timestamp")))
    .withColumn("review_timestamp", to_timestamp(col("review_timestamp")))
    .withColumn("decision_timestamp", to_timestamp(col("decision_timestamp")))
    .withColumn("settlement_timestamp", to_timestamp(col("settlement_timestamp")))
    .withColumn("closure_timestamp", to_timestamp(col("closure_timestamp")))
    .withColumn("requested_amount", col("requested_amount").cast("decimal(18,2)"))
    .withColumn("approved_amount", col("approved_amount").cast("decimal(18,2)"))
    .withColumn("reserve_amount", col("reserve_amount").cast("decimal(18,2)"))
    .withColumn("deductible_amount", col("deductible_amount").cast("decimal(18,2)"))
)

silver_claims.write.format("delta").mode("overwrite").saveAsTable(
    "silver_claimiq_claims"
)


# --------------------------------------------------
# 3. Silver Policies
# --------------------------------------------------

silver_policies = (
    policies_df
    .withColumn("policy_id", trim(col("policy_id")))
    .withColumn("policyholder_id", trim(col("policyholder_id")))
    .withColumn("product_id", trim(col("product_id")))
    .withColumn("coverage_type", trim(col("coverage_type")))
    .withColumn("policy_status", trim(col("policy_status")))
    .withColumn("region_code", trim(col("region_code")))
    .withColumn("currency_code", trim(col("currency_code")))
    .withColumn("policy_start_date", to_date(col("policy_start_date")))
    .withColumn("policy_end_date", to_date(col("policy_end_date")))
    .withColumn("coverage_limit", col("coverage_limit").cast("decimal(18,2)"))
    .withColumn("deductible_amount", col("deductible_amount").cast("decimal(18,2)"))
    .withColumn("premium_amount", col("premium_amount").cast("decimal(18,2)"))
)

silver_policies.write.format("delta").mode("overwrite").saveAsTable(
    "silver_claimiq_policies"
)


# --------------------------------------------------
# 4. Silver Policyholders
# --------------------------------------------------

silver_policyholders = (
    policyholders_df
    .withColumn("policyholder_id", trim(col("policyholder_id")))
    .withColumn("policyholder_segment", trim(col("policyholder_segment")))
    .withColumn("age_band", trim(col("age_band")))
    .withColumn("region_code", trim(col("region_code")))
    .withColumn("risk_band", trim(col("risk_band")))
    .withColumn("join_date", to_date(col("join_date")))
    .withColumn(
        "active_flag",
        when(lower(trim(col("active_flag").cast("string"))).isin(
            "true", "1", "yes"
        ), True)
        .when(lower(trim(col("active_flag").cast("string"))).isin(
            "false", "0", "no"
        ), False)
        .otherwise(None)
    )
)

silver_policyholders.write.format("delta").mode("overwrite").saveAsTable(
    "silver_claimiq_policyholders"
)


# --------------------------------------------------
# 5. Silver Products
# --------------------------------------------------

silver_products = (
    products_df
    .withColumn("product_id", trim(col("product_id")))
    .withColumn("product_name", trim(col("product_name")))
    .withColumn("product_category", trim(col("product_category")))
    .withColumn("coverage_type", trim(col("coverage_type")))
    .withColumn("currency_code", trim(col("currency_code")))
    .withColumn("coverage_limit", col("coverage_limit").cast("decimal(18,2)"))
    .withColumn(
        "deductible_default",
        col("deductible_default").cast("decimal(18,2)")
    )
    .withColumn("sla_target_days", col("sla_target_days").cast("int"))
)

silver_products.write.format("delta").mode("overwrite").saveAsTable(
    "silver_claimiq_products"
)


# --------------------------------------------------
# 6. Silver Providers
# --------------------------------------------------

silver_providers = (
    providers_df
    .withColumn("provider_id", trim(col("provider_id")))
    .withColumn("provider_type", trim(col("provider_type")))
    .withColumn("provider_region", trim(col("provider_region")))
    .withColumn("network_tier", trim(col("network_tier")))
    .withColumn("onboarding_date", to_date(col("onboarding_date")))
)

silver_providers.write.format("delta").mode("overwrite").saveAsTable(
    "silver_claimiq_providers"
)


# --------------------------------------------------
# 7. Silver Claim Payments
# --------------------------------------------------

silver_payments = (
    claim_payments_df
    .withColumn("payment_id", trim(col("payment_id")))
    .withColumn("claim_id", trim(col("claim_id")))
    .withColumn("provider_id", trim(col("provider_id")))
    .withColumn("payment_sequence", col("payment_sequence").cast("int"))
    .withColumn("payment_date", to_date(col("payment_date")))
    .withColumn("payment_status", trim(col("payment_status")))
    .withColumn("payment_method", trim(col("payment_method")))
    .withColumn("paid_amount", col("paid_amount").cast("decimal(18,2)"))
    .withColumn("currency_code", trim(col("currency_code")))
)

silver_payments.write.format("delta").mode("overwrite").saveAsTable(
    "silver_claimiq_claim_payments"
)


# --------------------------------------------------
# 8. Display Silver Tables
# --------------------------------------------------

display(spark.table("silver_claimiq_claims").limit(10))
display(spark.table("silver_claimiq_policies").limit(10))
display(spark.table("silver_claimiq_policyholders").limit(10))
display(spark.table("silver_claimiq_products").limit(10))
display(spark.table("silver_claimiq_providers").limit(10))
display(spark.table("silver_claimiq_claim_payments").limit(10))


# --------------------------------------------------
# 9. Record Count Validation
# --------------------------------------------------

print("Claims:", spark.table("silver_claimiq_claims").count())
print("Policies:", spark.table("silver_claimiq_policies").count())
print("Policyholders:", spark.table("silver_claimiq_policyholders").count())
print("Products:", spark.table("silver_claimiq_products").count())
print("Providers:", spark.table("silver_claimiq_providers").count())
print("Claim Payments:", spark.table("silver_claimiq_claim_payments").count())


# --------------------------------------------------
# 10. Claims Validation
# --------------------------------------------------

invalid_claims = (
    silver_claims
    .filter(
        (col("requested_amount") < 0) |
        (col("approved_amount") < 0) |
        (col("reserve_amount") < 0)
    )
)

display(invalid_claims)


# --------------------------------------------------
# 11. Policy Date Validation
# --------------------------------------------------

invalid_policies = (
    silver_policies
    .filter(col("policy_start_date") > col("policy_end_date"))
)

display(invalid_policies)


# --------------------------------------------------
# 12. Duplicate Claim Check
# --------------------------------------------------

duplicate_claims = (
    silver_claims
    .groupBy("claim_id")
    .count()
    .filter(col("count") > 1)
    .orderBy(desc("count"))
)

display(duplicate_claims)


# --------------------------------------------------
# 13. Bronze vs Silver Reconciliation
# --------------------------------------------------

datasets = [
    ("claims", "bronze_claimiq_claims", "silver_claimiq_claims"),
    ("policies", "bronze_claimiq_policies", "silver_claimiq_policies"),
    ("policyholders", "bronze_claimiq_policyholders", "silver_claimiq_policyholders"),
    ("products", "bronze_claimiq_products", "silver_claimiq_products"),
    ("providers", "bronze_claimiq_providers", "silver_claimiq_providers"),
    ("claim_payments", "bronze_claimiq_claim_payments",
     "silver_claimiq_claim_payments")
]

for name, bronze, silver in datasets:
    bronze_count = spark.table(bronze).count()
    silver_count = spark.table(silver).count()

    print(
        name,
        "Bronze =", bronze_count,
        "Silver =", silver_count,
        "Match =", bronze_count == silver_count
    )
