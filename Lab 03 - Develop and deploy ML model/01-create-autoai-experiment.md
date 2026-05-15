# Step 1: Create AutoAI Experiment

[← Back to Lab 03 Overview](./README.md) | [Next: Deploy Model →](./02-deploy-model.md)

---

## Overview

In this step, you will use IBM watsonx AutoAI to automatically build and train machine learning models for predicting customer repurchase behavior. AutoAI will test multiple algorithms and configurations to find the best performing model.

---

## 1.1 Create AutoAI Asset

1. Navigate to the **Asset** tab
2. Click the **Add Asset** button
3. Type `autoai` in the search field
4. Select **Build machine learning or RAG solution automatically**

<img width="1518" height="393" alt="image" src="https://github.com/user-attachments/assets/72284886-4eb5-4450-b9d2-c88c2e191b84" />

## 1.2 Select Model Type

1. Select **Build a machine learning model**
2. Click the **Next** button

<img width="1823" height="889" alt="image" src="https://github.com/user-attachments/assets/6f664025-00ec-4e14-9b21-53b2c0f4ca6b" />

## 1.3 Name Your Experiment

1. Set **Name** to: `Repurchase Model`
2. Click the **Create** button

<img width="1813" height="879" alt="image" src="https://github.com/user-attachments/assets/64d1c4b5-be7c-4f1b-a1cd-dea211392039" />

## 1.4 Add Training Data

1. In the **Add data source** page, click the **Select from project** button: <img width="143" height="21" alt="image" src="https://github.com/user-attachments/assets/37e63bf1-d1d1-49b9-b665-a7c1371627c0" />
2. When the **Select Data From Project** window appears:
   - Select **Connection**
   - Select **cos-connection**
   - Select your COS bucket name
   - Select **FEATURE_STORE.csv**
3. Click the **Select Asset** button

<img width="1795" height="901" alt="image" src="https://github.com/user-attachments/assets/c96ba54b-832b-4d87-bfef-81361af69968" />

## 1.5 Configure Prediction Target

1. Select **No** for the question "Create a time series analysis?"
2. Select **REPURCHASE** for the question "What do you want to predict?"
3. Click the **Experiment Settings** button

<img width="1876" height="861" alt="image" src="https://github.com/user-attachments/assets/e063274d-c287-4fb1-aa5e-29128bd9ad87" />

## 1.6 Configure Experiment Settings

Ensure the following values are set correctly:

### Prediction Type
- **Prediction type**: Binary classification

<img width="763" height="295" alt="image" src="https://github.com/user-attachments/assets/3997dc5f-dabf-42c0-a43b-e542a1414542" />

### Positive Class
- **Positive class**: "Y"

<img width="777" height="159" alt="image" src="https://github.com/user-attachments/assets/54cfc658-9c4e-4b67-aad3-2021293af33a" />

### Optimized Metric
- **Optimized metric**: Accuracy

<img width="775" height="420" alt="image" src="https://github.com/user-attachments/assets/9530d81b-190e-458c-95bd-7d60dd2cbea5" />

### Algorithms
- Leave **Algorithm to include** as default

<img width="761" height="620" alt="image" src="https://github.com/user-attachments/assets/d203cb45-9df7-4183-8f77-197cc00611b7" />

### Number of Algorithms
- **Algorithm to use**: 2

<img width="777" height="158" alt="image" src="https://github.com/user-attachments/assets/c0d2c659-fa64-474c-9c12-de110bb28a78" />

## 1.7 Configure Data Source Settings

1. Go to the **Data source** tab
2. Turn **OFF** the **Use date/time processing** slider
3. Turn **OFF** the **Use text feature engineering** slider

<img width="624" height="259" alt="image" src="https://github.com/user-attachments/assets/594aec62-21a3-4478-b291-92e9e2cfc0ea" />

## 1.8 Select Features

1. In the **Select Features To Include** section, exclude the following columns:
   - **CUSTOMER_ID**
   - **PURCHASE_PERIOD**
2. Click the **Save Settings** button

<img width="1779" height="890" alt="image" src="https://github.com/user-attachments/assets/ba464f8b-e763-47ee-ad1e-12450f93fd50" />

## 1.9 Run the Experiment

1. Click the **Run Experiment** button: <img width="121" height="31" alt="image" src="https://github.com/user-attachments/assets/00918a4c-f2c3-4d74-a5c6-28bfd4b5d97a" />
2. Wait until the process is completed

<img width="1920" height="800" alt="image" src="https://github.com/user-attachments/assets/d97693db-5b81-4a00-b36a-a281e5ee0a29" />

### Understanding the Results

The AutoAI experiment will generate multiple pipelines with different algorithms and configurations. You'll see information including:

- **Rank**: Performance ranking (1 is best)
- **Pipeline Name**: Unique identifier for each pipeline
- **Algorithm Name**: The ML algorithm used
- **Specialization**: Processing mode indicators
  - **INCR**: Incremental mode for optimized memory usage
- **Enhancement**: Additional optimizations applied
  - **HPO-1** or **HPO-2**: Hyperparameter optimization
  - **FE**: Feature engineering transformations
- **Optimized Metric**: The accuracy score
- **Build Time**: Time taken to train the model

<img width="1510" height="328" alt="image" src="https://github.com/user-attachments/assets/f5924a18-60b7-4fa2-8baf-690780c79579" />

## 1.10 Select Best Pipeline

1. Select the pipeline with the **highest rank** (in this example, it's Pipeline 5)
2. Click the **Save As** button

<img width="1818" height="66" alt="image" src="https://github.com/user-attachments/assets/8ffce624-052d-49b7-9258-3fac21f2e31d" />

## 1.11 Save the Model

1. Set **Asset Type** to: **Model**
2. Leave **Name** as default
3. Click the **Create** button

<img width="1768" height="891" alt="image" src="https://github.com/user-attachments/assets/8f7f01ba-8bd6-4da7-be13-09ed204ece54" />

**Success!** Your machine learning model has been created and saved to your project.

---

[← Back to Lab 03 Overview](./README.md) | [Next: Deploy Model →](./02-deploy-model.md)