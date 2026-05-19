# Step 2: Evaluate Model Performance

After configuring watsonx.governance, you'll evaluate your model using a testing dataset and analyze the results across fairness, quality, and drift metrics. You'll also explore explainability features to understand individual predictions.

---

## Prerequisites

- Completed [Step 1: Configure watsonx.governance](./01-configure-watsonx-governance.md)
- Testing dataset CSV file available in assets folder

---

## Upload Testing Dataset

**35.** Ensure you are in **Repurchase Model Endpoint Evaluation** tab → click **Action** button → click **Evaluate Now**

<img width="1684" height="823" alt="image" src="https://github.com/user-attachments/assets/be083cd9-a922-497a-a3d4-5ad69357542f" />

**36.** Set Import to **"from CSV file"** → select **"Repurchase Model Testing Dataset.csv"** under directory **"assets/"** → click **Upload and Evaluate** button → wait until process completed

<img width="752" height="757" alt="image" src="https://github.com/user-attachments/assets/d8bf76a8-facc-4894-83dd-8eab2a1377d1" />

---

## Review Evaluation Results

**37.** Below is the testing result. You will see results of:
- **Fairness analysis** (passed)
- **Quality analysis** (failed)
- **Drift analysis** (passed)

<img width="1681" height="719" alt="image" src="https://github.com/user-attachments/assets/ec9e2259-71ec-45ec-8a4c-fab6f347c559" />

---

## Analyze Quality Metrics

**38.** Since Quality analysis is not passed, let's deep dive into this metric by clicking **right-arrow icon** in Quality section

<img width="535" height="87" alt="image" src="https://github.com/user-attachments/assets/e93e3568-a826-42a7-91a8-812ff77cbdc7" />

**39.** Take a look at the metrics provided and check which metrics passed the test:
- **Area Under ROC** (Receiver Operating Characteristic)
- **Area under PR** (Precision-Recall)
- **Accuracy**
- **TPR** (True Positive Rate)
- **FPR** (False Positive Rate)
- **Recall**
- **Precision**
- **F1** Score
- **Logarithmic Loss**
- **Brier Score**
- **Gini Coefficient**

<img width="1687" height="304" alt="image" src="https://github.com/user-attachments/assets/ac06ae4d-b959-4a7a-84ef-35c82d07045b" />

---

## Examine Confusion Matrix

**40.** Scroll down to **Confusion Matrix** section → find how many testing data points were predicted correctly

<img width="1689" height="355" alt="image" src="https://github.com/user-attachments/assets/15f6139a-e37b-4c06-9ea3-6a677b74ab70" />

**Understanding the Confusion Matrix:**
- **True Positives (TP)**: Correctly predicted "Y" (will repurchase)
- **True Negatives (TN)**: Correctly predicted "N" (will not repurchase)
- **False Positives (FP)**: Incorrectly predicted "Y" (actually "N")
- **False Negatives (FN)**: Incorrectly predicted "N" (actually "Y")

---

## Analyze Individual Transactions

**41.** Scroll down to **Transaction Details** → set **Predicted Value** to **"Y"** and **Actual Value** to **"Y"**

<img width="1689" height="483" alt="image" src="https://github.com/user-attachments/assets/c27b96f5-ed73-4233-ac72-beb84d936e3d" />

**42.** Click **Analyze** <img width="62" height="21" alt="image" src="https://github.com/user-attachments/assets/5632b8aa-75ef-4fc1-9926-0fa9cf8106c9" /> on the first transaction → here you will see the input payload

<img width="1584" height="939" alt="image" src="https://github.com/user-attachments/assets/f991a4d7-07ea-458c-8557-eec319b6aa8f" />

---

## Generate Prediction Explanation

**43.** Click <img width="123" height="28" alt="image" src="https://github.com/user-attachments/assets/db8dc46a-b37b-4719-b3d6-34a81ceae7c2" /> in top side of the screen → click the number displayed under **Number of explanations**

<img width="1663" height="255" alt="image" src="https://github.com/user-attachments/assets/b6ec7a8f-dcc4-44f6-bf01-0acc415dc4de" />

**44.** Click **Explain**

<img width="1374" height="298" alt="image" src="https://github.com/user-attachments/assets/a9c7792a-f519-4400-9a32-1d6efa12bf0b" />

**45.** Here you will see features sorted by correlation value (highest positive and highest negative)

<img width="1391" height="756" alt="image" src="https://github.com/user-attachments/assets/9b96c93c-1a20-4990-8c97-561e4b35549f" />

**Understanding Feature Importance:**
- **Positive correlation**: Features that increase the likelihood of repurchase
- **Negative correlation**: Features that decrease the likelihood of repurchase
- **LIME explanation**: Shows which features most influenced this specific prediction

---

## Evaluation Complete

You have successfully:
- ✅ Uploaded testing dataset for evaluation
- ✅ Reviewed fairness, quality, and drift analysis results
- ✅ Examined detailed quality metrics
- ✅ Analyzed confusion matrix for prediction accuracy
- ✅ Investigated individual transaction predictions
- ✅ Generated explainability insights using LIME

---

## Key Insights

### Fairness Analysis (Passed)
The model shows no significant bias between monitored (Male) and reference (Female) groups, meeting the Statistical Parity Difference threshold.

### Quality Analysis (Failed)
Some quality metrics did not meet the configured thresholds. Review the specific metrics that failed and consider:
- Retraining the model with more data
- Adjusting feature engineering
- Tuning model hyperparameters
- Reviewing threshold configurations

### Drift Analysis (Passed)
No significant drift detected in input features or model predictions, indicating the model remains stable with current data patterns.

### Explainability
LIME provides local explanations showing which features most influenced individual predictions, helping build trust and understanding in model decisions.

---

## Next Steps

After completing this lab, proceed to:
- [Lab 05: Extend MLOps with Agentic AI](../Lab%2005%20-%20Extend%20MLOps%20with%20Agentic%20AI/README.md)

---

## Additional Resources

- [IBM watsonx.governance Documentation](https://www.ibm.com/docs/en/watsonx/saas?topic=governance-overview)
- [OpenScale Fairness Monitoring](https://www.ibm.com/docs/en/watsonx/saas?topic=monitors-fairness)
- [Model Quality Metrics](https://www.ibm.com/docs/en/watsonx/saas?topic=monitors-quality)
- [Drift Detection Guide](https://www.ibm.com/docs/en/watsonx/saas?topic=monitors-drift)
- [LIME Explainability](https://www.ibm.com/docs/en/watsonx/saas?topic=explanations-local-interpretable-model-agnostic)