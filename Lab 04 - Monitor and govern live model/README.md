# Lab 04: Monitor and Govern Live Model

Overview:
After machine learning model has been deployed, we continue to monitor it because we want to ensure its quality using certain metrics (accuracy, AUC, recall, precision, etc.). In this session we will use watsonx.governance to perform continuous model monitoring and governance.

## Configure watsonx.governance

1. From watsonx.ai home page, click Hamburger icon in top right side --> expand Deployment Spaces --> click View all deployment spaces

<img width="304" height="450" alt="image" src="https://github.com/user-attachments/assets/2884bf1e-6c38-4cf4-a7c0-f1259f2c9496" />

2. Select "Repurchase Model Deployment Space" or any deployment spaces that you have created in Lab 03

 <img width="513" height="123" alt="image" src="https://github.com/user-attachments/assets/75a26b4f-475a-4721-8117-365e04f10628" />

3. Go to Deployments tab --> select "Repurchase Model Endpoint"

<img width="1702" height="311" alt="image" src="https://github.com/user-attachments/assets/99cc3a77-d82a-4603-ac8a-71a0d730e10f" />

4. Go to Evaluations tab --> click Configure OpenScale evaluation settings button

<img width="1702" height="708" alt="image" src="https://github.com/user-attachments/assets/ebd14223-4673-43a2-b8f2-e57211159d77" />

5. Click View Summary button

<img width="1589" height="938" alt="image" src="https://github.com/user-attachments/assets/dc3495f0-9be3-4576-a292-b29289074d8e" />

6. Check "Allow service to create, use and store credentials via task credentials" checkbox --> click Finish button

<img width="1591" height="940" alt="image" src="https://github.com/user-attachments/assets/57730f9e-e00d-48bd-93ad-8b15d326e7ac" />

7. Click Pencil icon in Training Data section

<img width="1591" height="939" alt="image" src="https://github.com/user-attachments/assets/d68a423d-83be-4ba1-851d-a30218333878" />

8. Select "Use manual setup" under Configuration Setup section --> click Next button

<img width="1584" height="933" alt="image" src="https://github.com/user-attachments/assets/22d83d04-4e1d-4dc6-8410-baf89f176754" />

9. Click Upload --> select file named "Repurchase Model Training Dataset.csv" under directory "assets/" --> in Select directory choose "Comma (,)" --> click Next button

<img width="1593" height="943" alt="image" src="https://github.com/user-attachments/assets/81568e08-978d-4b67-bd0b-ad30fa7718a9" />

10. Ensure REPURCHASE column is set to Label/Target --> click Next button

<img width="1583" height="936" alt="image" src="https://github.com/user-attachments/assets/d301897f-3bf1-4956-bc2b-62fc5a2d0fc8" />

11. Ensure your view is same with image below --> click View Summary button

<img width="1584" height="939" alt="image" src="https://github.com/user-attachments/assets/bc7c1a28-fbfb-47ef-a1b8-9ef944e75e19" />

12. Ensure your Summary view is same with image below --> click Finish button

<img width="1580" height="937" alt="image" src="https://github.com/user-attachments/assets/0b463e0c-a555-4d5d-8d7a-0bb3fd184576" />

13. Click Fairness in left pane --> click Pencil icon in COnfiguration section

<img width="1585" height="898" alt="image" src="https://github.com/user-attachments/assets/a9d40302-6fbb-4b71-a316-9356cefa4588" />

14. Select Configure Manually --> click Next button

<img width="1588" height="893" alt="image" src="https://github.com/user-attachments/assets/f02d8370-a2d2-4f7a-8228-61edbbd7b254" />

15. Ensure "Y" is set as Favorable and "N" is set as Unfavorable --> click Next button

<img width="1589" height="892" alt="image" src="https://github.com/user-attachments/assets/668052e6-d35e-4a3e-8b89-c91c3aa856d1" />

16. Leave the configuration as default --> click Next button

<img width="1586" height="891" alt="image" src="https://github.com/user-attachments/assets/ad059251-c272-4e09-9e38-7156a7124dc6" />

17. Select Statistical Party Difference --> click Next button

<img width="1585" height="894" alt="image" src="https://github.com/user-attachments/assets/11614ecb-9b93-4b72-b180-637d2a23d691" />

18. Leave the configuration as default --> click Next button

<img width="1592" height="895" alt="image" src="https://github.com/user-attachments/assets/24e72dff-f998-4665-a797-e442357259bb" />

19. Ensure GENDER is checked --> click Next button

<img width="1588" height="891" alt="image" src="https://github.com/user-attachments/assets/851906fc-daa1-4233-8fde-98c5a430d091" />

20. Ensure "Male" is set to Monitored and Female is set to Reference --> click Next button

<img width="1589" height="893" alt="image" src="https://github.com/user-attachments/assets/6e934150-22a2-4a94-8183-fe49241db8fb" />

21. Select "Use default threshold" --> click Save button --> wait until setup has completed

<img width="1589" height="891" alt="image" src="https://github.com/user-attachments/assets/1056627a-328e-47b1-b821-56ddec859f32" />

22. Click Quality in left pane --> click Pencil icon in Quality Threshold section

<img width="1584" height="898" alt="image" src="https://github.com/user-attachments/assets/2790e6b9-2a2f-46a8-a3d9-891ed67b3d8b" />

23. Set the configuration threshold as default --> click Next button

<img width="1586" height="896" alt="image" src="https://github.com/user-attachments/assets/350c3f5f-c64c-4654-887c-af12a5270f35" />

24. Set Minimum Sample Size to 1000 --> click Save button --> wait until process completed

<img width="1586" height="894" alt="image" src="https://github.com/user-attachments/assets/a0c1fb8d-bc83-47a2-9e40-f1f49c7a8b61" />

25. Click Drift v2 in left pane --> click Pencil icon in Complete the drift archive section

<img width="1580" height="892" alt="image" src="https://github.com/user-attachments/assets/41175609-87fc-4efd-aa4a-e94bb9586f19" />

26. Set Compute Option to "Compute in Watson OpenScale" --> click Next button

<img width="1581" height="894" alt="image" src="https://github.com/user-attachments/assets/961f0661-095b-4572-a141-3eed1632ef9e" />

27. Leave the configuration as default --> click Next button

<img width="1581" height="892" alt="image" src="https://github.com/user-attachments/assets/62345eb0-4691-4c45-8fe7-0318eb2e6c9d" />

28. Select all features start with "TOTAL_" --> click Next button

<img width="1584" height="898" alt="image" src="https://github.com/user-attachments/assets/c104223e-4fce-4de7-9ede-061a21dac844" />

29. Select TOTAL_PURCHASE_AMOUNT_L12M_Mean and TOTAL_PURCHASE_AMOUNT_L12M_SUM for Most Important Features --> click Next button

<img width="1588" height="895" alt="image" src="https://github.com/user-attachments/assets/23ea6e8d-18d4-4698-a911-ffd94c83a7c5" />

30. Set Minimum Sample Size to 100 --> click Save button --> wait until process completed

<img width="1585" height="890" alt="image" src="https://github.com/user-attachments/assets/3438ed82-c89c-43d3-bf88-3ce382cabcd6" />

31. Click Explainability in left pane --> click Pencil icon

<img width="1591" height="897" alt="image" src="https://github.com/user-attachments/assets/76e0e3fa-95a6-420e-bec7-82bbd181303a" />

32. Set Local Explanation Method to LIME --> click Next button

<img width="1587" height="893" alt="image" src="https://github.com/user-attachments/assets/4a7b60e9-d01b-4fc6-9747-2bd8f7ee8d6d" />

33. Set Number of pertubations per records to 5000 --> click Next button

<img width="1585" height="891" alt="image" src="https://github.com/user-attachments/assets/a0f805df-9ab0-4de5-9df0-fcdd5fd4ca24" />

34. Unselect CUSTOMER_ID and PURCHASE_PERIOD --> click Save button --> wait until process has completed

<img width="1589" height="891" alt="image" src="https://github.com/user-attachments/assets/432c35f4-c05f-422f-a7f0-37963214fc43" />

## Set Testing Dataset and Understand watsonx.governance Analysis Result

35. Ensure you are in Repurchase Model Endpoint Evaluation tab --> click Action button --> click Evaluate Now

<img width="1684" height="823" alt="image" src="https://github.com/user-attachments/assets/be083cd9-a922-497a-a3d4-5ad69357542f" />

36. Set Import to "from CSV file" --> select "Repurchase Model Testing Dataset.csv" under directory "assets/" --> click Upload and Evaluate button --> wait until process completed

<img width="752" height="757" alt="image" src="https://github.com/user-attachments/assets/d8bf76a8-facc-4894-83dd-8eab2a1377d1" />

37. Below is the testing result. You will see result of Fairness analysis (passed), Quality analysis (failed) and Drift analysis (passed).

<img width="1681" height="719" alt="image" src="https://github.com/user-attachments/assets/ec9e2259-71ec-45ec-8a4c-fab6f347c559" />

38. Since Quality analysis is not passed, let's deep dive into this metric by clicking right-arrow icon in Quality section

<img width="535" height="87" alt="image" src="https://github.com/user-attachments/assets/e93e3568-a826-42a7-91a8-812ff77cbdc7" />

39. Take a look at some metrics provided (Area Under ROC, Area under PR, Accuracy, TPR, FPR, Recall, Precision, F1, Logaritmic Loss, Brier Score, and Gini Coefficient) and check which metrics that are passed the test

<img width="1687" height="304" alt="image" src="https://github.com/user-attachments/assets/ac06ae4d-b959-4a7a-84ef-35c82d07045b" />

40. Scroll down to Confusion Matrix section --> find how many testing data predicted correctly

<img width="1689" height="355" alt="image" src="https://github.com/user-attachments/assets/15f6139a-e37b-4c06-9ea3-6a677b74ab70" />

41. Scroll down to Transaction Details --> set Predicted Value to "Y" and Actual Value to "Y"

<img width="1689" height="483" alt="image" src="https://github.com/user-attachments/assets/c27b96f5-ed73-4233-ac72-beb84d936e3d" />

42. Click Analyze <img width="62" height="21" alt="image" src="https://github.com/user-attachments/assets/5632b8aa-75ef-4fc1-9926-0fa9cf8106c9" /> on the first transaction --> here you will see the input payload

<img width="1584" height="939" alt="image" src="https://github.com/user-attachments/assets/f991a4d7-07ea-458c-8557-eec319b6aa8f" />

43. Click <img width="123" height="28" alt="image" src="https://github.com/user-attachments/assets/db8dc46a-b37b-4719-b3d6-34a81ceae7c2" /> in top side of the screen --> click number displayed under Number of explanations

<img width="1663" height="255" alt="image" src="https://github.com/user-attachments/assets/b6ec7a8f-dcc4-44f6-bf01-0acc415dc4de" />

44. Click Explain

<img width="1374" height="298" alt="image" src="https://github.com/user-attachments/assets/a9c7792a-f519-4400-9a32-1d6efa12bf0b" />

45. Here you will see features sorted by correlation value (highest positive and highest negative)

<img width="1391" height="756" alt="image" src="https://github.com/user-attachments/assets/9b96c93c-1a20-4990-8c97-561e4b35549f" />

