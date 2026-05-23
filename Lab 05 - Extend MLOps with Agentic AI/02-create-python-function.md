# Step 2: Create Python Function

[← Back to Lab 05 Overview](./README.md) | [Previous: Create AgentLab ←](./01-create-agentlab.md)

---

## Overview

In this step, you will create a custom Python function that:
1. Deploys Python Engine in Deployment Space
2. Retrieves customer feature store data by Customer ID
3. Sends input payload to the Repurchase Model endpoint for predictions

---

## 2.1 Deploy Python Engine

1. Scroll down to **Tools** section
2. Click **Create custom tool** button

<img width="879" height="118" alt="image" src="https://github.com/user-attachments/assets/a3589add-df98-4bca-a9cf-5f67b3bbb442" />

3. Click **Deploy Python Engine**

<img width="1784" height="70" alt="image" src="https://github.com/user-attachments/assets/b6507d46-a63f-48a0-9ef5-c1d4d1555331" />

4. Set **Deployment Space** to **"Repurchase Model Deployment Space"**
5. Click **Create** button
6. Wait for process to complete
7. Close the window

<img width="1778" height="889" alt="image" src="https://github.com/user-attachments/assets/25ce9d22-1c45-47b0-aa29-4d0a465d314a" />

---

## 2.2 Get COS Connection ID

1. Go to **Asset** tab
2. Find and click **cos-connection** asset (created in Lab 01)

<img width="1567" height="57" alt="image" src="https://github.com/user-attachments/assets/48ac1602-6765-496e-8ae6-fb3fb89122c5" />

3. Copy the **connection ID** from your URL:
   - Format: `https://dataplatform.cloud.ibm.com/connections/xxx`
   - `xxx` is your connection ID
   - Example: `019e2aa3-bf42-72a5-a4bc-3349c3ff499c`

<img width="1914" height="729" alt="image" src="https://github.com/user-attachments/assets/3942d28d-b161-464e-8886-dd2ff7e98ea4" />

---

## 2.3 Open Agent for Editing

1. Go back to **Asset** tab
2. Click **Repurchase Agent** to open it
3. Click **Edit** button

<img width="689" height="247" alt="image" src="https://github.com/user-attachments/assets/b9ddcc13-637c-472a-8ba2-c0b5b82c3b1c" />

4. Scroll down to **Tools** section
5. Click **Create Custom Tool** button

<img width="877" height="112" alt="image" src="https://github.com/user-attachments/assets/e1e3d7ce-74cd-4074-8331-f5c258dfcc99" />

---

## 2.4 Configure Secrets

1. Go to **Configure** tab
2. Click **Add Secret** button <img width="128" height="31" alt="image" src="https://github.com/user-attachments/assets/4108a151-eb46-4480-87ec-c93dd2697f4d" />
3. Set:
   - **Name**: `COS_CONNECTION_ID`
   - **Value**: Connection ID from step 2.2
4. Click **Create Secret** button

<img width="1802" height="900" alt="image" src="https://github.com/user-attachments/assets/6a72acd3-d9fc-4e74-95be-b37a51e7aa1d" />

5. Add the following additional secrets:

| Name | Value | Source |
|------|-------|--------|
| `WATSONX_API_KEY` | Your API Key | Created in Lab 01, Step 2.3 |
| `WATSONX_URL` | Your current region | Refer to this [link](https://www.ibm.com/docs/en/watsonx/saas?topic=ai-service-endpoints) |
| `WATSONX_PROJECT_ID` | Your Project ID | From URL: `https://dataplatform.cloud.ibm.com/wx/agents/<agent_id>?project_id=<project_id>&context=wx` |
| `REPURCHASE_MODEL_ENDPOINT` | Model endpoint URL | From Lab 03, Step 2.10 |
| `COS_BUCKET_NAME` | `FEATURE_STORE.csv` | Feature store generated from Lab 02, Step 3.4.13 |
| `COS_FEATURE_STORE_FILENAME` | Your bucket name where you store Feature Store | Open this [link](./02.1-get-cos-bucket-name.md) to know your bucket name |

6. After setup, you should have all secrets configured:

<img width="1525" height="406" alt="image" src="https://github.com/user-attachments/assets/97d7e301-7e11-438f-8697-6aa538d4af5c" />

---

## 2.5 Define Custom Tool

1. Go to **Define** tab
2. Set **Name** to: `Get Customer Feature Values`
3. Set **Description** to: `Tool to retrieve feature values from the Feature Store table using the provided Customer ID.`

4. Set **Input JSON Schema** to:
```json
{
 "customer_id": {
  "title": "Customer ID",
  "description": "Customer ID",
  "type": "string"
 },
 "report_date": {
  "title": "Report Date",
  "description": "Date when feature store is created",
  "type": "string"
 }
}
```

5. Set **Python Code** to:
```python
from ibm_watsonx_ai import APIClient

import pandas as pd
from sqlalchemy import create_engine
from ibm_watsonx_ai import APIClient
from io import BytesIO
import ibm_boto3
import requests

credentials = {
    "url": WATSONX_URL,
    "apikey": WATSONX_API_KEY
}

# Create client
client = APIClient(credentials)

# Set project
client.set.default_project(WATSONX_PROJECT_ID)

def main(customer_id, report_date):  
  def query_csv_using_watsonx_connection(
      credentials,
      project_id,
      connection_id,
      bucket_name,
      file_name,
      sql_query
  ):
      """
      Query CSV file from IBM Cloud Object Storage
      using Watsonx.ai APIClient connection asset.
  
      Parameters
      ----------
      credentials : dict
          Watsonx.ai credentials
  
      project_id : str
          Watsonx.ai project ID
  
      connection_id : str
          Watsonx.ai connection asset ID
  
      bucket_name : str
          COS bucket name
  
      file_name : str
          CSV file path/name inside bucket
  
      sql_query : str
          SQL query to execute
  
      Returns
      -------
      pandas.DataFrame
      """
  
      try:
          # Initialize Watsonx client
          client = APIClient(credentials)
  
          # Set project
          client.set.default_project(project_id)
  
          # Get connection details
          conn_details = client.connections.get_details(connection_id)
  
          # Extract COS properties
          props = conn_details["entity"]["properties"]
  
          api_key = props["api_key"]
          resource_instance_id = props["resource_instance_id"]
          endpoint_url = "https://" + props["url"]
  
          # Create COS client
          print("hehe")
          cos_client = ibm_boto3.client(
              "s3",
              ibm_api_key_id=api_key,
              ibm_service_instance_id=resource_instance_id,
              config=ibm_boto3.session.Config(
                  signature_version="oauth"
              ),
              endpoint_url=endpoint_url
          )
  
          print("hehe")
  
          # Read object from COS
          obj = cos_client.get_object(
              Bucket=bucket_name,
              Key=file_name
          )
  
          # Load CSV into dataframe
          df = pd.read_csv(
              BytesIO(obj["Body"].read())
          )
  
          # Create temporary SQLite engine
          engine = create_engine("sqlite://", echo=False)
  
          # Save dataframe into temporary SQL table
          df.to_sql(
              "customer_data",
              engine,
              index=False,
              if_exists="replace"
          )
  
          # Execute SQL query
          result_df = pd.read_sql_query(
              sql_query,
              engine
          )
  
          return result_df
  
      except Exception as e:
          print(f"Error occurred: {str(e)}")
          return None
        
  sql_query = f"""
  SELECT *
  FROM customer_data
  WHERE CUSTOMER_ID = {customer_id} AND PURCHASE_PERIOD = '{report_date}'
  """
  
  result = query_csv_using_watsonx_connection(
      credentials=credentials,
      project_id=WATSONX_PROJECT_ID,
      connection_id=COS_CONNECTION_ID,
      bucket_name=COS_FEATURE_STORE_FILENAME,
      file_name=COS_FEATURE_STORE_FILENAME,
      sql_query=sql_query
  )

  result_list = [0 if v is None else v for v in result.values[0].tolist() if v not in ['Y', 'N']]

  API_KEY = WATSONX_API_KEY
  token_response = requests.post('https://iam.cloud.ibm.com/identity/token', data={"apikey": API_KEY, "grant_type": 'urn:ibm:params:oauth:grant-type:apikey'})
  mltoken = token_response.json()["access_token"]
  
  header = {'Content-Type': 'application/json', 'Authorization': 'Bearer ' + mltoken}
  
  # NOTE:  manually define and pass the array(s) of values to be scored in the next line
  payload_scoring = {
      "input_data": [
          {
              "fields": [
                  "CUSTOMER_ID",
                  "PURCHASE_PERIOD",
                  "TOTAL_PURCHASE_AMOUNT_L3M_Sum",
                  "TOTAL_PURCHASE_AMOUNT_L3M_Mean",
                  "TOTAL_PURCHASE_AMOUNT_L3M_Median",
                  "TOTAL_PURCHASE_AMOUNT_L6M_Sum",
                  "TOTAL_PURCHASE_AMOUNT_L6M_Mean",
                  "TOTAL_PURCHASE_AMOUNT_L6M_Median",
                  "TOTAL_PURCHASE_AMOUNT_L12M_Sum",
                  "TOTAL_PURCHASE_AMOUNT_L12M_Mean",
                  "TOTAL_PURCHASE_AMOUNT_L12M_Median",
                  "GENDER"
              ],
              "values": [result_list]
          }
      ]
  }
  
  response_scoring = requests.post(REPURCHASE_MODEL_ENDPOINT, json=payload_scoring,
   headers={'Authorization': 'Bearer ' + mltoken})
  
  return response_scoring.json()
```

<img width="1760" height="710" alt="image" src="https://github.com/user-attachments/assets/3f597d7c-f1f7-494a-8bb7-3cd9f70b6231" />

---

## 2.6 Test Custom Tool

1. Go to **Test** tab
2. Use this test payload:
```json
{
 "customer_id": "1",
 "report_date": "2020-03-31"
}
```

3. Click **Run** button <img width="87" height="21" alt="image" src="https://github.com/user-attachments/assets/d29e7212-32d6-466c-a581-90d113ede27b" />
4. Verify you get a successful result:

<img width="1772" height="887" alt="image" src="https://github.com/user-attachments/assets/785b46a7-70df-41df-a82a-39116c5f6494" />

5. Click **Save** button <img width="62" height="29" alt="image" src="https://github.com/user-attachments/assets/8963521c-7d8d-411f-ac59-0e7fc2120c19" />

---

## 2.7 Test Agent with Natural Language

1. Test the agent with this query:
   ```
   get repurchase prediction from customer id 1 as of 31 march 2020
   ```

2. Verify the agent:
   - Understands your natural language query
   - Calls the custom tool
   - Responds with human-readable prediction

<img width="1849" height="885" alt="image" src="https://github.com/user-attachments/assets/75bfd9fe-ea8a-48e5-9c61-2f3482d59000" />

---

## 2.8 Deploy Agent (Optional)

1. Click **Deploy** button <img width="107" height="28" alt="image" src="https://github.com/user-attachments/assets/e06a69bc-067f-4a4f-ac49-dfbae2337ce8" />
2. Follow the deployment steps to make the agent available as an API for third-party applications

---

## Custom Tool Complete

You have successfully:
- ✅ Deployed Python Engine
- ✅ Configured secrets for API access
- ✅ Created custom tool to retrieve customer features
- ✅ Integrated with model endpoint for predictions
- ✅ Tested agent with natural language queries
- ✅ Enabled agent for API deployment

---

[← Back to Lab 05 Overview](./README.md) | [Previous: Create AgentLab ←](./01-create-agentlab.md)
