# Lab 03: Develop and Deploy Machine Learning Model

This lab guides you through building and deploying a machine learning model using IBM watsonx AutoAI. You'll create an automated ML experiment to predict customer repurchase behavior and deploy it as a real-time API endpoint.

---

## Overview

In this lab, you will:
- Use AutoAI to automatically build and train ML models
- Configure experiment settings for binary classification
- Select the best performing model from multiple pipelines
- Deploy the model to a deployment space
- Create an online endpoint for real-time predictions
- Test the deployed model with sample data

---

## Lab Steps

### [Step 1: Create AutoAI Experiment](./01-create-autoai-experiment.md)
Build and train machine learning models automatically using IBM watsonx AutoAI.

**What you'll do:**
- Create an AutoAI experiment
- Configure training data from FEATURE_STORE.csv
- Set up binary classification for REPURCHASE prediction
- Configure experiment settings (algorithms, metrics, features)
- Run the experiment and select the best model
- Save the trained model to your project

**Key Configurations:**
- **Prediction Type**: Binary classification
- **Target Variable**: REPURCHASE (Y/N)
- **Optimized Metric**: Accuracy
- **Excluded Features**: CUSTOMER_ID, PURCHASE_PERIOD

---

### [Step 2: Deploy Model](./02-deploy-model.md)
Deploy your trained model and create an API endpoint for real-time predictions.

**What you'll do:**
- Promote model to a deployment space
- Create a new deployment space
- Deploy model as an online endpoint
- Review API documentation and sample code
- Test the deployment with sample data
- View prediction results

**Deployment Details:**
- **Deployment Type**: Online (real-time)
- **Endpoint Name**: Repurchase Model Endpoint
- **API Support**: REST API with multiple language examples

---

## Prerequisites

Before starting this lab, ensure you have:
- Completed [Lab 02: Perform EDA and Feature Engineering](../Lab%2002%20-%20Perform%20EDA%20and%20feature%20engineering/README.md)
- FEATURE_STORE.csv available in your Cloud Object Storage
- Access to IBM watsonx platform
- Understanding of machine learning concepts

---

## Expected Outcomes

By the end of this lab, you will have:
- ✅ Created an AutoAI experiment for repurchase prediction
- ✅ Trained multiple ML models automatically
- ✅ Selected and saved the best performing model
- ✅ Created a deployment space
- ✅ Deployed the model as an online endpoint
- ✅ Tested the model with real data
- ✅ Obtained API credentials for model integration

**Key Outputs:**
- Trained ML model saved in project
- Deployed model endpoint (REST API)
- API documentation and sample code
- Test predictions demonstrating model performance

---

## Key Concepts

**AutoAI** is IBM's automated machine learning capability that:
- Automatically prepares data
- Selects appropriate algorithms
- Engineers features
- Tunes hyperparameters
- Ranks models by performance

**Binary Classification** predicts one of two possible outcomes:
- **Positive Class (Y)**: Customer will repurchase
- **Negative Class (N)**: Customer will not repurchase

**Online Deployment** provides:
- Real-time predictions via REST API
- Low latency responses
- Scalable infrastructure
- Integration with applications

---

## Next Steps

After completing this lab, proceed to:
- [Lab 04: Monitor and Govern Live Model](../Lab%2004%20-%20Monitor%20and%20govern%20live%20model/README.md)

---

## Additional Resources

- [IBM watsonx AutoAI Documentation](https://www.ibm.com/docs/en/watsonx/saas?topic=models-autoai)
- [Model Deployment Guide](https://www.ibm.com/docs/en/watsonx/saas?topic=models-deploying)
- [REST API Reference](https://cloud.ibm.com/apidocs/machine-learning)
