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

Notes:
This process will select best algorithm to predict customer customer who will make repurchase transaction. You can see several information such as Rank, Pipeline Name, Algorithm Name, Specialization, Optimized Metric, Enhancement and Build Time. Here is the additional notes for each information.

* If you see "INCR" in Specialization, it means that the pipeline is running in incremental mode to optimize memory usage when developing ML model. When
* If Enhancement has "HPO-1" or "HPO-2", it means the pipeline is running in hyperparameterization mode
* If Enhancement has "FE", it means the pipeline is creating data transformation to create new feature

<img width="1510" height="328" alt="image" src="https://github.com/user-attachments/assets/f5924a18-60b7-4fa2-8baf-690780c79579" />

10. Select pipeline which has highest rank (for my case it is Pipeline 5) --> click Save As button

<img width="1818" height="66" alt="image" src="https://github.com/user-attachments/assets/8ffce624-052d-49b7-9258-3fac21f2e31d" />

11. Set Asset Type to Model --> set Name as default --> click Create button

<img width="1768" height="891" alt="image" src="https://github.com/user-attachments/assets/8f7f01ba-8bd6-4da7-be13-09ed204ece54" />

## Deploy Model

12. Go to Asset tab --> hover your mouse to AutoAI model that you have just saved --> click 3-dots icon --> select Promote to space

<img width="1505" height="141" alt="image" src="https://github.com/user-attachments/assets/a4b45ce3-83a9-4aa5-9b04-7ecbf45bb4e2" />

13. First, you have to Create a new deployment space

<img width="635" height="122" alt="image" src="https://github.com/user-attachments/assets/9c5606a7-9e60-4ea0-9ade-232fc219c9a3" />

14. Set Name to "Repurchase Model Deployment Space" --> select Storage with your COS instance --> select watsonx.ai Runtime with your watsonx.ai instance --> click Create button

<img width="1664" height="809" alt="image" src="https://github.com/user-attachments/assets/98679888-a918-41b3-ac94-0ba0bb58e22d" />

15. Click Promote button

<img width="1780" height="897" alt="image" src="https://github.com/user-attachments/assets/c413ebe1-2bf1-4bd7-81e6-d3df7f5eddcb" />

16. Click Hmaburger icon in top left side --> expand Deployment space --> select View all deployment space

<img width="302" height="464" alt="image" src="https://github.com/user-attachments/assets/90d10372-25e9-423d-aea9-ea73fe297fe3" />

17. Go to Spaces tab --> select Repurchase Model Deployment Space

<img width="573" height="316" alt="image" src="https://github.com/user-attachments/assets/1697c10b-5a9a-45c6-8b98-6a7204942fb5" />

18. Go to Assets tab --> hover your mouse to your model --> click 3-dots icon --> select Deploy

<img width="1887" height="410" alt="image" src="https://github.com/user-attachments/assets/cb62e9b0-781e-43c0-b63c-bfd682c1feb5" />

19. Set Deployment Type to Online --> set Name to "Repurchase Model Endpoint" --> click Create button

<img width="1781" height="894" alt="image" src="https://github.com/user-attachments/assets/57159f0c-ae0e-40f0-b9cd-8c26adadbcd4" />

20. Once the endpoint is ready, click it

<img width="1569" height="227" alt="image" src="https://github.com/user-attachments/assets/01addb4f-fab0-4021-9632-fe48abb9827c" />

21. In this API Reference tab you will find documentation how to call this endpoint. Several information is as below:
    * Private and Public endpoint
    * Sample code to call the endpoint that can be: cURL, Java, Javascript, Python, Scala

<img width="1566" height="822" alt="image" src="https://github.com/user-attachments/assets/bc481209-36a2-42d8-be9b-ef3b36c7a5eb" />

22. Download this file Repurchase Model Endpoint_test_input.csv

23. Go to Test tab --> select Text tab --> click Browse local files <img width="148" height="28" alt="image" src="https://github.com/user-attachments/assets/16801bac-e200-4072-b914-652509014a33" /> --> select files that you have downloaded prevously --> verify data appears in the table --> click Predict button

<img width="1846" height="742" alt="image" src="https://github.com/user-attachments/assets/4c26b8fe-2585-4c3b-b911-23eea316d8cc" />

24. Once the prediction completed, you can see the prediction result

<img width="1784" height="898" alt="image" src="https://github.com/user-attachments/assets/e85c879f-17cc-4662-bebf-d27a0a778a93" />
