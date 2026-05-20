# Step 2: Deploy Model

[← Previous: Create AutoAI Experiment](./01-create-autoai-experiment.md) | [Back to Lab 03 Overview](./README.md)

---

## Overview

In this step, you will deploy your trained machine learning model to a deployment space and create an online endpoint for real-time predictions. This makes your model accessible via API for integration with applications.

---

## 2.1 Promote Model to Deployment Space

1. Navigate to the **Asset** tab
2. Hover your mouse over the AutoAI model you just saved
3. Click the **3-dots icon** (⋮)
4. Select **Promote to space**

<img width="1505" height="141" alt="image" src="https://github.com/user-attachments/assets/a4b45ce3-83a9-4aa5-9b04-7ecbf45bb4e2" />

## 2.2 Create Deployment Space

Since this is your first deployment, you need to create a new deployment space:

1. Click **Create a new deployment space**

<img width="635" height="122" alt="image" src="https://github.com/user-attachments/assets/9c5606a7-9e60-4ea0-9ade-232fc219c9a3" />

## 2.3 Configure Deployment Space

1. Set **Name** to: `Repurchase Model Deployment Space`
2. Select **Storage** with your COS instance
3. Select **watsonx.ai Runtime** with your watsonx.ai instance
4. Click the **Create** button

<img width="1664" height="809" alt="image" src="https://github.com/user-attachments/assets/98679888-a918-41b3-ac94-0ba0bb58e22d" />

## 2.4 Promote the Model

- Click the **Promote** button to move your model to the deployment space

<img width="1780" height="897" alt="image" src="https://github.com/user-attachments/assets/c413ebe1-2bf1-4bd7-81e6-d3df7f5eddcb" />

## 2.5 Navigate to Deployment Spaces

1. Click the **Hamburger icon** (☰) in the top left corner
2. Expand **Deployment space**
3. Select **View all deployment space**

<img width="302" height="464" alt="image" src="https://github.com/user-attachments/assets/90d10372-25e9-423d-aea9-ea73fe297fe3" />

## 2.6 Open Your Deployment Space

1. Go to the **Spaces** tab
2. Select **Repurchase Model Deployment Space**

<img width="573" height="316" alt="image" src="https://github.com/user-attachments/assets/1697c10b-5a9a-45c6-8b98-6a7204942fb5" />

## 2.7 Deploy the Model

1. Go to the **Assets** tab
2. Hover your mouse over your model
3. Click the **3-dots icon** (⋮)
4. Select **Deploy**

<img width="1887" height="410" alt="image" src="https://github.com/user-attachments/assets/cb62e9b0-781e-43c0-b63c-bfd682c1feb5" />

## 2.8 Configure Deployment

1. Set **Deployment Type** to: **Online**
2. Set **Name** to: `Repurchase Model Endpoint`
3. Click the **Create** button

<img width="1781" height="894" alt="image" src="https://github.com/user-attachments/assets/57159f0c-ae0e-40f0-b9cd-8c26adadbcd4" />

## 2.9 Access the Deployment

1. Wait for the endpoint status to show as **Ready**
2. Click on the deployment name to open it

<img width="1569" height="227" alt="image" src="https://github.com/user-attachments/assets/01addb4f-fab0-4021-9632-fe48abb9827c" />

## 2.10 Review API Reference

In the **API Reference** tab, you'll find comprehensive documentation for calling your endpoint:

**Available Information:**
- **Private and Public endpoints**: URLs for accessing your model. _Note: Save Public endpoint as you will use it in Lab 05._
- **Sample code** in multiple languages:
  - cURL
  - Java
  - JavaScript
  - Python
  - Scala

<img width="1566" height="822" alt="image" src="https://github.com/user-attachments/assets/bc481209-36a2-42d8-be9b-ef3b36c7a5eb" />

## 2.11 Prepare Test Data

Download the test input file:
- **File**: `Repurchase Model Endpoint_test_input.csv`
- **Location**: `Lab 03 - Develop and deploy ML model/assets/Repurchase Model Endpoint_test_input.csv`
- Save it to your local machine

## 2.12 Test the Deployment

1. Go to the **Test** tab
2. Select the **File** tab
3. Click **Browse local files**: <img width="148" height="28" alt="image" src="https://github.com/user-attachments/assets/16801bac-e200-4072-b914-652509014a33" />
4. Select the file you downloaded previously
5. Verify the data appears in the table
6. Click the **Predict** button

<img width="1846" height="742" alt="image" src="https://github.com/user-attachments/assets/4c26b8fe-2585-4c3b-b911-23eea316d8cc" />

## 2.13 View Prediction Results

Once the prediction is completed, you can see the prediction results including:
- **Predicted values**: Whether customers will repurchase (Y/N)
- **Confidence scores**: Probability for each prediction
- **Input features**: The data used for prediction

<img width="1784" height="898" alt="image" src="https://github.com/user-attachments/assets/e85c879f-17cc-4662-bebf-d27a0a778a93" />

**Congratulations!** Your machine learning model is now deployed and ready to make real-time predictions.

---

## What's Next?

Your deployed model can now be:
- Integrated into applications via REST API
- Used for batch predictions
- Monitored for performance and drift
- Updated with new training data

---

[← Previous: Create AutoAI Experiment](./01-create-autoai-experiment.md) | [Back to Lab 03 Overview](./README.md) | [Next: Lab 04 - Monitor and Govern Live Model →](../Lab%2004%20-%20Monitor%20and%20govern%20live%20model/README.md)
