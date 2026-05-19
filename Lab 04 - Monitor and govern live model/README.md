# Lab 04: Monitor and Govern Live Model

This lab guides you through implementing continuous monitoring and governance for your deployed machine learning model using IBM watsonx.governance. You'll configure monitoring for fairness, quality, drift, and explainability to ensure your model performs reliably in production.

---

## Overview

After deploying a machine learning model, continuous monitoring is essential to ensure it maintains quality and fairness over time. In this lab, you will:
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
- Understanding of ML evaluation metrics

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
- Insights into model behavior and feature importance

---

## Key Concepts

### watsonx.governance
IBM's AI governance platform that provides:
- **Continuous Monitoring**: Track model performance over time
- **Fairness Detection**: Identify and mitigate bias
- **Quality Assurance**: Ensure models meet performance standards
- **Drift Detection**: Alert when data or behavior changes
- **Explainability**: Understand model decisions

### Monitoring Dimensions

**Fairness Monitoring**
- Detects bias across demographic groups (gender, age, etc.)
- Uses Statistical Parity Difference metric
- Compares monitored vs. reference groups
- Alerts when bias exceeds thresholds

**Quality Monitoring**
- Tracks 11+ performance metrics
- Includes accuracy, precision, recall, F1, ROC AUC
- Monitors confusion matrix changes
- Alerts when quality degrades

**Drift Detection**
- Monitors input feature distributions
- Detects model behavior changes
- Tracks most important features
- Alerts when drift exceeds thresholds

**Explainability**
- Uses LIME (Local Interpretable Model-agnostic Explanations)
- Shows feature importance for individual predictions
- Identifies positive and negative correlations
- Builds trust through transparency

---

## Evaluation Results Interpretation

### Fairness Analysis
- **Passed**: No significant bias detected between groups
- **Failed**: Bias exceeds configured threshold
- **Action**: Review model training data and feature engineering

### Quality Analysis
- **Passed**: All metrics meet configured thresholds
- **Failed**: One or more metrics below threshold
- **Action**: Consider retraining, feature engineering, or threshold adjustment

### Drift Analysis
- **Passed**: Data distribution remains stable
- **Failed**: Significant drift detected in features or predictions
- **Action**: Investigate data changes, consider model retraining

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
- [AI Governance Best Practices](https://www.ibm.com/topics/ai-governance)
