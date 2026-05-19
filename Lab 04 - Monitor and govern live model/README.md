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

15. Ensure "Y" is set as Favorable and "N" is set as Unfavorable

<img width="1589" height="892" alt="image" src="https://github.com/user-attachments/assets/668052e6-d35e-4a3e-8b89-c91c3aa856d1" />

