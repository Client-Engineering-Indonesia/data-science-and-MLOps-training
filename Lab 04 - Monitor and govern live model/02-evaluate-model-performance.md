# Step 2: Evaluate Model Performance

[← Back to Lab 04 Overview](./README.md) | [Previous: Configure watsonx.governance ←](./01-configure-watsonx-governance.md)

---

## Overview

In this step, you will evaluate your model using a testing dataset and analyze the results across fairness, quality, and drift metrics. You'll also explore explainability features to understand individual predictions.

---

## 2.1 Upload Testing Dataset

1. Ensure you are in **Repurchase Model Endpoint Evaluation** tab
2. Click **Action** button
3. Click **Evaluate Now**

<img width="1684" height="823" alt="image" src="https://github.com/user-attachments/assets/be083cd9-a922-497a-a3d4-5ad69357542f" />

4. Set Import to **"from CSV file"**
5. Select **"Repurchase Model Testing Dataset.csv"** from **"assets/"** directory
6. Click **Upload and Evaluate** button
7. Wait until process completed

<img width="752" height="757" alt="image" src="https://github.com/user-attachments/assets/d8bf76a8-facc-4894-83dd-8eab2a1377d1" />

---

## 2.2 Review Evaluation Results

1. Review the testing results showing:
   - **Fairness analysis** (passed)
   - **Quality analysis** (failed)
   - **Drift analysis** (passed)

<img width="1681" height="719" alt="image" src="https://github.com/user-attachments/assets/ec9e2259-71ec-45ec-8a4c-fab6f347c559" />

---

## 2.3 Analyze Quality Metrics

1. Click **right-arrow icon** in Quality section to deep dive into the metrics

<img width="535" height="87" alt="image" src="https://github.com/user-attachments/assets/e93e3568-a826-42a7-91a8-812ff77cbdc7" />

2. Review the quality metrics:
   - Area Under ROC
   - Area under PR
   - Accuracy
   - TPR (True Positive Rate)
   - FPR (False Positive Rate)
   - Recall
   - Precision
   - F1 Score
   - Logarithmic Loss
   - Brier Score
   - Gini Coefficient

3. Check which metrics passed the test

<img width="1687" height="304" alt="image" src="https://github.com/user-attachments/assets/ac06ae4d-b959-4a7a-84ef-35c82d07045b" />

---

## 2.4 Examine Confusion Matrix

1. Scroll down to **Confusion Matrix** section
2. Review how many testing data points were predicted correctly

<img width="1689" height="355" alt="image" src="https://github.com/user-attachments/assets/15f6139a-e37b-4c06-9ea3-6a677b74ab70" />

---

## 2.5 Analyze Individual Transactions

1. Scroll down to **Transaction Details**
2. Set **Predicted Value** to **"Y"**
3. Set **Actual Value** to **"Y"**

<img width="1689" height="483" alt="image" src="https://github.com/user-attachments/assets/c27b96f5-ed73-4233-ac72-beb84d936e3d" />

4. Click **Analyze** <img width="62" height="21" alt="image" src="https://github.com/user-attachments/assets/5632b8aa-75ef-4fc1-9926-0fa9cf8106c9" /> on the first transaction
5. Review the input payload

<img width="1584" height="939" alt="image" src="https://github.com/user-attachments/assets/f991a4d7-07ea-458c-8557-eec319b6aa8f" />

---

## 2.6 Generate Prediction Explanation

1. Click <img width="123" height="28" alt="image" src="https://github.com/user-attachments/assets/db8dc46a-b37b-4719-b3d6-34a81ceae7c2" /> in top side of the screen
2. Click the number displayed under **Number of explanations**

<img width="1663" height="255" alt="image" src="https://github.com/user-attachments/assets/b6ec7a8f-dcc4-44f6-bf01-0acc415dc4de" />

3. Click **Explain**

<img width="1374" height="298" alt="image" src="https://github.com/user-attachments/assets/a9c7792a-f519-4400-9a32-1d6efa12bf0b" />

4. Review features sorted by correlation value (highest positive and highest negative)

<img width="1391" height="756" alt="image" src="https://github.com/user-attachments/assets/9b96c93c-1a20-4990-8c97-561e4b35549f" />

---

## Evaluation Complete

You have successfully:
- ✅ Uploaded testing dataset for evaluation
- ✅ Reviewed fairness, quality, and drift analysis results
- ✅ Examined detailed quality metrics
- ✅ Analyzed confusion matrix
- ✅ Investigated individual transaction predictions
- ✅ Generated explainability insights using LIME

---

[← Back to Lab 04 Overview](./README.md) | [Previous: Configure watsonx.governance ←](./01-configure-watsonx-governance.md)