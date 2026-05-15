# Lab 02: Perform EDA and Feature Engineering

This lab guides you through exploratory data analysis (EDA) and feature engineering using IBM watsonx and SPSS Modeler. You'll learn how to analyze customer purchase data, create time-based aggregations, and build a comprehensive feature store for machine learning.

---

## Overview

In this lab, you will:
- Create SPSS Modeler assets for data processing
- Perform exploratory data analysis on customer purchase data
- Engineer features including monthly aggregations for 3, 6, and 12-month periods
- Build a base user dataset with repurchase labels
- Create a comprehensive feature store for model training

---

## Lab Steps

### [Step 1: Create SPSS Modeler Asset](./01-create-spss-modeler.md)
Learn how to create and configure an SPSS Modeler asset in your watsonx project.

### [Step 2: Perform Exploratory Data Analysis](./02-exploratory-data-analysis.md)
Analyze customer purchase data to understand patterns, distributions, and data quality.

### [Step 3: Perform Feature Engineering](./03-feature-engineering.md)
Create sophisticated features through multiple sub-steps:
- **[3.1 Monthly Purchase Transaction Table](./03-1-monthly-purchase-table.md)** - Aggregate transactions by month
- **[3.2 Time-Based Aggregations](./03-2-time-based-aggregations.md)** - Create 3, 6, and 12-month features
- **[3.3 Base User Dataset](./03-3-base-user-dataset.md)** - Build labeled dataset for training
- **[3.4 Feature Store](./03-4-feature-store.md)** - Combine all features into final dataset

---

## Prerequisites

Before starting this lab, ensure you have:
- Completed [Lab 01: Create your first watsonx project](../Lab%2001%20-%20Create%20your%20first%20watsonx%20project/README.md)
- Access to IBM watsonx platform
- Customer purchase data uploaded to Cloud Object Storage
- Basic understanding of data analysis concepts

---

## Expected Outcomes

By the end of this lab, you will have:
- ✅ Performed comprehensive EDA on customer purchase data
- ✅ Created monthly aggregated purchase transactions
- ✅ Generated time-based feature sets (3, 6, and 12 months)
- ✅ Built a labeled base user dataset for supervised learning
- ✅ Created a feature store ready for model training

**Key Outputs:**
- `CUSTOMER_MONTHLY_PURCHASE.csv` - Monthly aggregated transactions
- `CUSTOMER_PURCHASE_L3M.csv` - 3-month aggregations
- `CUSTOMER_PURCHASE_L6M.csv` - 6-month aggregations
- `CUSTOMER_PURCHASE_L12M.csv` - 12-month aggregations
- `BASE_USER.csv` - Labeled dataset with repurchase indicators
- `FEATURE_STORE.csv` - Final feature store for ML training

---

## Next Steps

After completing this lab, proceed to:
- [Lab 03: Develop and Deploy ML Model](../Lab%2003%20-%20Develop%20and%20deploy%20ML%20model/README.md)

---

## Additional Resources

- [IBM watsonx Documentation](https://www.ibm.com/docs/en/watsonx)
- [SPSS Modeler Documentation](https://www.ibm.com/docs/en/spss-modeler)
- [Feature Engineering Best Practices](https://www.ibm.com/topics/feature-engineering)
