# Step 5: Create Db2 Database Connection

[← Previous: Associate watsonx Service](./04-associate-watsonx-service.md) | [Back to Lab 01 Overview](./README.md) | [Next: Create Cloud Object Storage Connection →](./06-create-cos-connection.md)

---

## 5.1 Start Connection Setup
1. Navigate to the **Asset** tab
2. Click the **New asset** button: <img width="149" height="52" alt="image" src="https://github.com/user-attachments/assets/dd5171ad-7312-4b44-976a-47dd550b405c" />
3. Find and click **Connect to a data source**

<img width="321" height="242" alt="image" src="https://github.com/user-attachments/assets/893b5b23-d88a-4a75-91b3-9f63fa389808" />

## 5.2 Select Database Type
1. In the **Search** field, type: `db2`
2. Select **IBM Db2** from the search results
3. Confirm that **IBM Db2** is highlighted in the right panel
4. Click the **Next** button

<img width="1815" height="879" alt="image" src="https://github.com/user-attachments/assets/2100b52e-a198-44a2-b58c-92f2e10d1451" />

## 5.3 Name Your Connection
- In the **Connection overview** section, set **Name** to: `db2-connection`

<img width="1021" height="475" alt="image" src="https://github.com/user-attachments/assets/20183ff1-5a9e-43b2-9cd5-1fb520bd6012" />

## 5.4 Configure Database Connection Details
Enter the following connection information:
- **Hostname**: `54a2f15b-5c0f-46df-8954-7e38e612c2bd.c1ogj3sd0tgtu0lqde00.databases.appdomain.cloud`
- **Port**: `32733`
- **Database**: `bludb`

<img width="1066" height="600" alt="image" src="https://github.com/user-attachments/assets/37cadecb-e65d-4e96-9142-e46eb72cbf66" />

## 5.5 Enter Database Credentials
- **Username**: `rsh14813`
- **Password**: `NVNoNqfRzMEe0Zvi`

<img width="1018" height="237" alt="image" src="https://github.com/user-attachments/assets/0213a29f-1997-4008-a51c-0c5601d9ef19" />

## 5.6 Configure SSL Settings
1. Check the **Port is SSL-Enabled** checkbox
2. Copy and paste the following **SSL Certificate**:
   ```
   LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSURFakNDQWZxZ0F3SUJBZ0lKQVA1S0R3ZTNCTkxiTUEwR0NTcUdTSWIzRFFFQkN3VUFNQjR4SERBYUJnTlYKQkFNTUUwbENUU0JEYkc5MVpDQkVZWFJoWW1GelpYTXdIaGNOTWpBd01qSTVNRFF5TVRBeVdoY05NekF3TWpJMgpNRFF5TVRBeVdqQWVNUnd3R2dZRFZRUUREQk5KUWswZ1EyeHZkV1FnUkdGMFlXSmhjMlZ6TUlJQklqQU5CZ2txCmhraUc5dzBCQVFFRkFBT0NBUThBTUlJQkNnS0NBUUVBdXUvbitpWW9xdkdGNU8xSGpEalpsK25iYjE4UkR4ZGwKTzRUL3FoUGMxMTREY1FUK0plRXdhdG13aGljTGxaQnF2QWFMb1hrbmhqSVFOMG01L0x5YzdBY291VXNmSGR0QwpDVGcrSUsxbjBrdDMrTHM3d1dTakxqVE96N3M3MlZUSU5yYmx3cnRIRUlvM1JWTkV6SkNHYW5LSXdZMWZVSUtrCldNMlR0SDl5cnFsSGN0Z2pIUlFmRkVTRmlYaHJiODhSQmd0amIva0xtVGpCaTFBeEVadWNobWZ2QVRmNENOY3EKY21QcHNqdDBPTnI0YnhJMVRyUWxEemNiN1hMSFBrWW91SUprdnVzMUZvaTEySmRNM1MrK3labFZPMUZmZkU3bwpKMjhUdGJoZ3JGOGtIU0NMSkJvTTFSZ3FPZG9OVm5QOC9EOWZhamNNN0lWd2V4a0lSOTNKR1FJREFRQUJvMU13ClVUQWRCZ05WSFE0RUZnUVVlQ3JZanFJQzc1VUpxVmZEMDh1ZWdqeDZiUmN3SHdZRFZSMGpCQmd3Rm9BVWVDclkKanFJQzc1VUpxVmZEMDh1ZWdqeDZiUmN3RHdZRFZSMFRBUUgvQkFVd0F3RUIvekFOQmdrcWhraUc5dzBCQVFzRgpBQU9DQVFFQUkyRTBUOUt3MlN3RjJ2MXBqaHV4M0lkWWV2SGFVSkRMb0tPd0hSRnFSOHgxZ2dRcGVEcFBnMk5SCkx3R08yek85SWZUMmhLaWd1d2orWnJ5SGxxcHlxQ0pLOHJEU28xZUVPekIyWmE2S1YrQTVscEttMWdjV3VHYzMKK1UrVTFzTDdlUjd3ZFFuVjU0TVU4aERvNi9sVHRMRVB2Mnc3VlNPSlFDK013ejgrTFJMdjVHSW5BNlJySWNhKwozM0wxNnB4ZEttd1pLYThWcnBnMXJ3QzRnY3dlYUhYMUNEWE42K0JIbzhvWG5YWkh6UG91cldYS1BoaGdXZ2J5CkNDcUdIK0NWNnQ1eFg3b05NS3VNSUNqRVZndnNLWnRqeTQ5VW5iNVZZbHQ0b1J3dTFlbGdzRDNjekltbjlLREQKNHB1REFvYTZyMktZZE4xVkxuN3F3VG1TbDlTU05RPT0KLS0tLS1FTkQgQ0VSVElGSUNBVEUtLS0tLQo=
   ```

<img width="1023" height="305" alt="image" src="https://github.com/user-attachments/assets/6acc79a8-e3fb-4ea8-9eba-4dce1192fc3f" />

## 5.7 Test and Save Connection
1. Click the **Test connection** button: <img width="207" height="48" alt="image" src="https://github.com/user-attachments/assets/6f688830-f0c0-44eb-bfaf-fdd7be1fa013" />
2. Wait for the success message:
   > "The test was successful. Click Create to save the connection information."
3. Click the **Create** button to save your connection: <img width="87" height="35" alt="image" src="https://github.com/user-attachments/assets/cfdf517c-6817-4077-8c99-100c41b23815" />

<img width="555" height="48" alt="image" src="https://github.com/user-attachments/assets/aa056f83-36a1-4315-9a3e-e0d00eae4f52" />

---

[← Previous: Associate watsonx Service](./04-associate-watsonx-service.md) | [Back to Lab 01 Overview](./README.md) | [Next: Create Cloud Object Storage Connection →](./06-create-cos-connection.md)