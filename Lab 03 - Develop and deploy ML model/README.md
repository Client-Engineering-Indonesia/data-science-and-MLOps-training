# Lab 03: Develop and Deploy Machine Learning Model

## Create AutoAI 

1. Go to Asset tab --> click Add Asset button --> type "autoai" in search field --> select Build machine learning or RAG solution automatically

<img width="1518" height="393" alt="image" src="https://github.com/user-attachments/assets/72284886-4eb5-4450-b9d2-c88c2e191b84" />

2. Select Build a machine learning model --> click Next button

<img width="1823" height="889" alt="image" src="https://github.com/user-attachments/assets/6f664025-00ec-4e14-9b21-53b2c0f4ca6b" />

3. Set Name to "Repurchase Model" --> click Create button

<img width="1813" height="879" alt="image" src="https://github.com/user-attachments/assets/64d1c4b5-be7c-4f1b-a1cd-dea211392039" />

4. In Add data source page, click Select from project button <img width="143" height="21" alt="image" src="https://github.com/user-attachments/assets/37e63bf1-d1d1-49b9-b665-a7c1371627c0" /> --> after Select Data From Project window appears, select Connection, select cos-connection, select your COS bucket name, select FEATURE_STORE.csv --> click Select Asset button

<img width="1795" height="901" alt="image" src="https://github.com/user-attachments/assets/c96ba54b-832b-4d87-bfef-81361af69968" />

5. Select No for question "Create a time series analysis?" question --> select REPURCHASE for question "What do you want to predict?" --> click Experiment Settings button

<img width="1876" height="861" alt="image" src="https://github.com/user-attachments/assets/e063274d-c287-4fb1-aa5e-29128bd9ad87" />

6. Ensure several values below:
  * Prediction type is Binary classification
    <img width="763" height="295" alt="image" src="https://github.com/user-attachments/assets/3997dc5f-dabf-42c0-a43b-e542a1414542" />

  * Positive class is "Y"
    <img width="777" height="159" alt="image" src="https://github.com/user-attachments/assets/54cfc658-9c4e-4b67-aad3-2021293af33a" />

  * Optimized metric is Accuracy
    <img width="775" height="420" alt="image" src="https://github.com/user-attachments/assets/9530d81b-190e-458c-95bd-7d60dd2cbea5" />
  
  * Leave Algorithm to include as default
    <img width="761" height="620" alt="image" src="https://github.com/user-attachments/assets/d203cb45-9df7-4183-8f77-197cc00611b7" />

  * Algorithm to use is 2
    <img width="777" height="158" alt="image" src="https://github.com/user-attachments/assets/c0d2c659-fa64-474c-9c12-de110bb28a78" />

7. Go to Data source tab --> tick-off Use date/time processing slider --> tick-off Use text feature engineering slider

<img width="624" height="259" alt="image" src="https://github.com/user-attachments/assets/594aec62-21a3-4478-b291-92e9e2cfc0ea" />

8. Exclude CUSTOMER_ID and PURCHASE_PERIOD in Select Features To Include section --> click Save Settings button

<img width="1779" height="890" alt="image" src="https://github.com/user-attachments/assets/ba464f8b-e763-47ee-ad1e-12450f93fd50" />

9. Click Run Experiment button <img width="121" height="31" alt="image" src="https://github.com/user-attachments/assets/00918a4c-f2c3-4d74-a5c6-28bfd4b5d97a" /> --> wait until process completed

<img width="1920" height="800" alt="image" src="https://github.com/user-attachments/assets/d97693db-5b81-4a00-b36a-a281e5ee0a29" />

10. 
