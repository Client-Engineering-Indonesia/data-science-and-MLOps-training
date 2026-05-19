# Lab 04: Monitor and Govern Live Model

This lab guides you through implementing continuous monitoring and governance for your deployed machine learning model using IBM watsonx.governance. You'll configure monitoring for fairness, quality, drift, and explainability to ensure your model performs reliably in production.

---

## Overview

In this lab, you will:
- Configure watsonx.governance for your deployed model
- Set up monitoring for fairness, quality, and drift
- Enable explainability features using LIME
- Evaluate model performance with testing data
- Analyze detailed metrics and individual predictions
- Understand model behavior through feature importance

---

## Lab Steps

### [Step 1: Configure watsonx.governance](./01-configure-watsonx-governance.md)
Set up comprehensive monitoring and governance for your deployed model.

**What you'll do:**
- Access your deployment space and model endpoint
- Initialize OpenScale evaluation settings
- Configure training data reference
- Set up fairness monitoring for gender bias detection
- Configure quality thresholds for performance metrics
- Enable drift detection for data and model changes
- Configure explainability using LIME method

**Key Configurations:**
- **Training Data**: Reference dataset for baseline comparisons
- **Fairness**: Statistical Parity Difference monitoring on GENDER
- **Quality**: Minimum sample size of 1000 for evaluation
- **Drift**: Monitor features starting with "TOTAL_"
- **Explainability**: LIME with 5000 perturbations per record

---

### [Step 2: Evaluate Model Performance](./02-evaluate-model-performance.md)
Test your model with a testing dataset and analyze comprehensive evaluation results.

**What you'll do:**
- Upload testing dataset for evaluation
- Review fairness, quality, and drift analysis results
- Examine detailed quality metrics (accuracy, precision, recall, etc.)
- Analyze confusion matrix for prediction accuracy
- Investigate individual transaction predictions
- Generate explainability insights for specific predictions

**Evaluation Metrics:**
- **Fairness**: Bias detection across demographic groups
- **Quality**: 11+ performance metrics including ROC, AUC, F1
- **Drift**: Data and model behavior changes
- **Explainability**: Feature importance for individual predictions

---

## Prerequisites

Before starting this lab, ensure you have:
- Completed [Lab 03: Develop and Deploy ML Model](../Lab%2003%20-%20Develop%20and%20deploy%20ML%20model/README.md)
- Deployed model endpoint running in a deployment space
- Training dataset CSV file (Repurchase Model Training Dataset.csv)
- Testing dataset CSV file (Repurchase Model Testing Dataset.csv)

---

## Expected Outcomes

By the end of this lab, you will have:
- ✅ Configured comprehensive model monitoring
- ✅ Set up fairness monitoring for bias detection
- ✅ Established quality thresholds for performance tracking
- ✅ Enabled drift detection for data changes
- ✅ Configured explainability for prediction transparency
- ✅ Evaluated model with testing data
- ✅ Analyzed detailed performance metrics
- ✅ Generated explanations for individual predictions

**Key Outputs:**
- Fully configured watsonx.governance monitoring
- Evaluation results across fairness, quality, and drift
- Detailed confusion matrix and metric analysis
- LIME-based explanations for predictions

---

## Key Concepts

**watsonx.governance** provides AI governance capabilities including:
- **Continuous Monitoring**: Track model performance over time
- **Fairness Detection**: Identify and mitigate bias
- **Quality Assurance**: Ensure models meet performance standards
- **Drift Detection**: Alert when data or behavior changes
- **Explainability**: Understand model decisions

**Fairness Monitoring** detects bias across demographic groups using Statistical Parity Difference metric.

**Quality Monitoring** tracks 11+ performance metrics including accuracy, precision, recall, F1, and ROC AUC.

**Drift Detection** monitors input feature distributions and model behavior changes.

**Explainability** uses LIME (Local Interpretable Model-agnostic Explanations) to show feature importance for individual predictions.

---

## Next Steps

After completing this lab, proceed to:
- [Lab 05: Extend MLOps with Agentic AI](../Lab%2005%20-%20Extend%20MLOps%20with%20Agentic%20AI/README.md)

---

## Additional Resources

- [IBM watsonx.governance Documentation](https://www.ibm.com/docs/en/watsonx/saas?topic=governance-overview)
- [OpenScale Fairness Monitoring](https://www.ibm.com/docs/en/watsonx/saas?topic=monitors-fairness)
- [Model Quality Metrics Guide](https://www.ibm.com/docs/en/watsonx/saas?topic=monitors-quality)
- [Drift Detection Documentation](https://www.ibm.com/docs/en/watsonx/saas?topic=monitors-drift)
- [LIME Explainability Guide](https://www.ibm.com/docs/en/watsonx/saas?topic=explanations-local-interpretable-model-agnostic)
