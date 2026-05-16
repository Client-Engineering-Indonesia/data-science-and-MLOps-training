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

7. Click pencil icon <img width="23" height="30" alt="image" src="https://github.com/user-attachments/assets/e89a4de6-bb87-4dec-9ed3-292f84a2b536" /> inside Training Data section

<img width="1582" height="835" alt="image" src="https://github.com/user-attachments/assets/80d92cef-4a6c-4269-8903-708b9238ad7b" />

8. Select Use manual setup --> click Next button

<img width="1590" height="938" alt="image" src="https://github.com/user-attachments/assets/ef208927-aacf-49e1-885d-735c3eec810d" />
