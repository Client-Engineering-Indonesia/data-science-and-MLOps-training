# Step 3: Perform Feature Engineering

[← Back to Lab 02 Overview](./README.md) | [← Previous: Exploratory Data Analysis](./02-exploratory-data-analysis.md)

---

## Overview

In this step, you will perform comprehensive feature engineering to prepare data for machine learning model development. This involves creating time-based aggregations, building a labeled dataset, and constructing a feature store.

---

## Feature Engineering Steps

### [3.1 Create Monthly Purchase Transaction Table](./03-1-monthly-purchase-table.md)
**Objective:** Aggregate purchase transactions on a monthly basis to enable end-of-month model execution.

**What you'll do:**
- Create SPSS Modeler asset for monthly aggregation
- Use Derive node to convert purchase dates to end-of-month periods
- Aggregate transactions by customer, gender, and purchase period
- Export results to Cloud Object Storage

**Output:** `CUSTOMER_MONTHLY_PURCHASE.csv`

---

### [3.2 Create Time-Based Aggregations (3, 6, and 12 Months)](./03-2-time-based-aggregations.md)
**Objective:** Create purchase transaction aggregations for different time periods to capture customer behavior patterns.

**What you'll do:**
- Use CUSTOMER_MONTHLY_PURCHASE.csv as base table
- Create 3-month aggregation with mean, sum, and median calculations
- Duplicate and modify for 6-month aggregation
- Duplicate and modify for 12-month aggregation
- Export all aggregated datasets

**Outputs:** 
- `CUSTOMER_PURCHASE_L3M.csv`
- `CUSTOMER_PURCHASE_L6M.csv`
- `CUSTOMER_PURCHASE_L12M.csv`

---

### [3.3 Create Base User Dataset](./03-3-base-user-dataset.md)
**Objective:** Create a ground truth dataset with repurchase labels for supervised learning.

**What you'll do:**
- Sort and process monthly purchase data
- Use History node to identify subsequent purchases
- Create REPURCHASE label (Y/N) based on 6-month window
- Filter and standardize columns
- Export labeled dataset

**Labels:**
- **"N"**: Customer did NOT repurchase in the next 6 months
- **"Y"**: Customer DID repurchase in the next 6 months

**Output:** `BASE_USER.csv`

---

### [3.4 Create Feature Store](./03-4-feature-store.md)
**Objective:** Build a comprehensive feature store combining all engineered features for model training.

**What you'll do:**
- Merge BASE_USER with 3-month aggregations
- Merge with 6-month aggregations
- Merge with 12-month aggregations
- Add GENDER variable from monthly purchase data
- Export final feature store

**Output:** `FEATURE_STORE.csv` - Ready for ML model training

---

## Key Concepts

**Feature Engineering** is the process of transforming raw data into features that better represent the underlying problem to predictive models, resulting in improved model accuracy.

**Time-Based Features** capture temporal patterns in customer behavior:
- **L3M (Last 3 Months)**: Recent short-term behavior
- **L6M (Last 6 Months)**: Medium-term trends
- **L12M (Last 12 Months)**: Long-term patterns

**Feature Store** is a centralized repository that stores curated features for machine learning, ensuring consistency between training and inference.

---

## Navigation

- [← Previous: Exploratory Data Analysis](./02-exploratory-data-analysis.md)
- [→ Next: Lab 03 - Develop and Deploy ML Model](../Lab%2003%20-%20Develop%20and%20deploy%20ML%20model/README.md)
- [↑ Back to Lab 02 Overview](./README.md)

---

## Quick Links to Subsections

1. [3.1 Monthly Purchase Transaction Table](./03-1-monthly-purchase-table.md)
2. [3.2 Time-Based Aggregations (3, 6, 12 Months)](./03-2-time-based-aggregations.md)
3. [3.3 Base User Dataset](./03-3-base-user-dataset.md)
4. [3.4 Feature Store](./03-4-feature-store.md)
