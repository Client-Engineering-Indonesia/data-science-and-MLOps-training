# Create Your First watsonx Project

**Prerequisites:**
Ensure you have received your credentials for this lab.

## Get Familiar watsonx

1. Open link provided in your credentials --> enter username and password --> click Signin button

<img width="418" height="433" alt="Screenshot 2026-05-15 at 11 01 45 AM" src="https://github.com/user-attachments/assets/d93fb5c4-dcb5-4645-96b1-e35c5b87624a" />

2. Click hamburger icon in top left side --> click Resouce list

<img width="418" height="433" alt="Screenshot 2026-05-15 at 11 01 45 AM" src="https://github.com/user-attachments/assets/eb6d6da7-f3f2-47a3-97b9-8d1b4a80c0c9" />

3. Expand AI / Machine Learning section --> click service name with Product named "watsonx.ai Runtime" --> in my case service name is "itzws-664004cgmn-9e5s2su9"

<img width="1823" height="230" alt="image" src="https://github.com/user-attachments/assets/64cb5b3f-76d0-490b-862a-e6787c7bbcbf" />

4. Click down arrow icon inside Launch in button --> click IBM watsonx

<img width="1906" height="519" alt="image" src="https://github.com/user-attachments/assets/ffa5d84e-9b55-4044-a059-e1dc731e66a4" />

5. Close Welcome page if you see it

<img width="959" height="506" alt="image" src="https://github.com/user-attachments/assets/7606ddbb-5309-44fe-8222-aab053be944d" />

### Create watsonx API Key

6. Click your profile icon in top right side --> select Profile and settings

<img width="383" height="206" alt="image" src="https://github.com/user-attachments/assets/d7f6c8e8-4603-4370-bce2-501b5311a776" />

7. Go to User API key tab --> click Create a key

<img width="1792" height="685" alt="image" src="https://github.com/user-attachments/assets/f36850e0-2154-4d6f-b63b-f1d004ed4c5f" />

8. Ensure you can see message "User API key is successfully created. Your new key is stored in IBM watsonx and IBM Cloud."

<img width="861" height="75" alt="image" src="https://github.com/user-attachments/assets/83f53b56-7c67-4846-9495-cd7d99d9e80d" />

### Create watsonx project

9. Go back to watsonx main page by clicking <img width="112" height="36" alt="image" src="https://github.com/user-attachments/assets/b44e98d1-e58f-43ff-95ff-3c988eaeddab" /> --> Scroll down until you find Projects section --> click + icon

<img width="1137" height="903" alt="image" src="https://github.com/user-attachments/assets/53238ddc-6485-4ae4-8a10-8f01ffd601ff" />

10. Set Name to "Churn Model" --> click Create button

<img width="1920" height="943" alt="image" src="https://github.com/user-attachments/assets/5ad5d34a-c2a4-41ee-80e3-4fad40650d5d" />

### Create connection

11. Go to Asset tab --> click <img width="149" height="52" alt="image" src="https://github.com/user-attachments/assets/dd5171ad-7312-4b44-976a-47dd550b405c" /> --> find Connect to a data source and click it

<img width="321" height="242" alt="image" src="https://github.com/user-attachments/assets/893b5b23-d88a-4a75-91b3-9f63fa389808" />

12. Type "db2" in Search field --> select IBM Db2 --> ensure IBM Db2 in right page is selected --> click Next button

<img width="1815" height="879" alt="image" src="https://github.com/user-attachments/assets/2100b52e-a198-44a2-b58c-92f2e10d1451" />

13. Set Name to "db2-connection" in Connection overview section

<img width="1021" height="475" alt="image" src="https://github.com/user-attachments/assets/20183ff1-5a9e-43b2-9cd5-1fb520bd6012" />

14. Set Hostname to "54a2f15b-5c0f-46df-8954-7e38e612c2bd.c1ogj3sd0tgtu0lqde00.databases.appdomain.cloud" --> Set Port to "32733" --> Set Database to "bludb"

<img width="1066" height="600" alt="image" src="https://github.com/user-attachments/assets/37cadecb-e65d-4e96-9142-e46eb72cbf66" />

15. Set Username to "rsh14813" --> set Password to "NVNoNqfRzMEe0Zvi"

<img width="1018" height="237" alt="image" src="https://github.com/user-attachments/assets/0213a29f-1997-4008-a51c-0c5601d9ef19" />

16. Tick-on Port is SSL-Enabled --> set SSL Certificate to "LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSURFakNDQWZxZ0F3SUJBZ0lKQVA1S0R3ZTNCTkxiTUEwR0NTcUdTSWIzRFFFQkN3VUFNQjR4SERBYUJnTlYKQkFNTUUwbENUU0JEYkc5MVpDQkVZWFJoWW1GelpYTXdIaGNOTWpBd01qSTVNRFF5TVRBeVdoY05NekF3TWpJMgpNRFF5TVRBeVdqQWVNUnd3R2dZRFZRUUREQk5KUWswZ1EyeHZkV1FnUkdGMFlXSmhjMlZ6TUlJQklqQU5CZ2txCmhraUc5dzBCQVFFRkFBT0NBUThBTUlJQkNnS0NBUUVBdXUvbitpWW9xdkdGNU8xSGpEalpsK25iYjE4UkR4ZGwKTzRUL3FoUGMxMTREY1FUK0plRXdhdG13aGljTGxaQnF2QWFMb1hrbmhqSVFOMG01L0x5YzdBY291VXNmSGR0QwpDVGcrSUsxbjBrdDMrTHM3d1dTakxqVE96N3M3MlZUSU5yYmx3cnRIRUlvM1JWTkV6SkNHYW5LSXdZMWZVSUtrCldNMlR0SDl5cnFsSGN0Z2pIUlFmRkVTRmlYaHJiODhSQmd0amIva0xtVGpCaTFBeEVadWNobWZ2QVRmNENOY3EKY21QcHNqdDBPTnI0YnhJMVRyUWxEemNiN1hMSFBrWW91SUprdnVzMUZvaTEySmRNM1MrK3labFZPMUZmZkU3bwpKMjhUdGJoZ3JGOGtIU0NMSkJvTTFSZ3FPZG9OVm5QOC9EOWZhamNNN0lWd2V4a0lSOTNKR1FJREFRQUJvMU13ClVUQWRCZ05WSFE0RUZnUVVlQ3JZanFJQzc1VUpxVmZEMDh1ZWdqeDZiUmN3SHdZRFZSMGpCQmd3Rm9BVWVDclkKanFJQzc1VUpxVmZEMDh1ZWdqeDZiUmN3RHdZRFZSMFRBUUgvQkFVd0F3RUIvekFOQmdrcWhraUc5dzBCQVFzRgpBQU9DQVFFQUkyRTBUOUt3MlN3RjJ2MXBqaHV4M0lkWWV2SGFVSkRMb0tPd0hSRnFSOHgxZ2dRcGVEcFBnMk5SCkx3R08yek85SWZUMmhLaWd1d2orWnJ5SGxxcHlxQ0pLOHJEU28xZUVPekIyWmE2S1YrQTVscEttMWdjV3VHYzMKK1UrVTFzTDdlUjd3ZFFuVjU0TVU4aERvNi9sVHRMRVB2Mnc3VlNPSlFDK013ejgrTFJMdjVHSW5BNlJySWNhKwozM0wxNnB4ZEttd1pLYThWcnBnMXJ3QzRnY3dlYUhYMUNEWE42K0JIbzhvWG5YWkh6UG91cldYS1BoaGdXZ2J5CkNDcUdIK0NWNnQ1eFg3b05NS3VNSUNqRVZndnNLWnRqeTQ5VW5iNVZZbHQ0b1J3dTFlbGdzRDNjekltbjlLREQKNHB1REFvYTZyMktZZE4xVkxuN3F3VG1TbDlTU05RPT0KLS0tLS1FTkQgQ0VSVElGSUNBVEUtLS0tLQo="

<img width="1023" height="305" alt="image" src="https://github.com/user-attachments/assets/6acc79a8-e3fb-4ea8-9eba-4dce1192fc3f" />

17. Click <img width="207" height="48" alt="image" src="https://github.com/user-attachments/assets/6f688830-f0c0-44eb-bfaf-fdd7be1fa013" /> and ensure there is message "The test was successful.
Click Create to save the connection information." --> click Create button <img width="87" height="35" alt="image" src="https://github.com/user-attachments/assets/cfdf517c-6817-4077-8c99-100c41b23815" />

<img width="555" height="48" alt="image" src="https://github.com/user-attachments/assets/aa056f83-36a1-4315-9a3e-e0d00eae4f52" />


