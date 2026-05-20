# Lab 05: Extend MLOps with Agentic AI

Overview:
In this lab you will develop Agentic AI using AgentLab in watsonx.ai. 
The output is chat interface where user can ask the prediction from certain CustomerID using human natural language.

## Create AgentLab

1. Go back to your latest project that you have built by go clicking Hamburger icon --> expand Projects --> click View all projects

<img width="268" height="284" alt="image" src="https://github.com/user-attachments/assets/6822bf77-ad8c-4903-be04-d61c470dbfec" />

2. Select latest project --> click Assets tab --> click New Assets button <img width="114" height="27" alt="image" src="https://github.com/user-attachments/assets/f78c15ec-674d-4d93-a272-172441e30d0c" /> --> type "agent" in search field --> select Build an AI agent to automate tasks

<img width="1607" height="441" alt="image" src="https://github.com/user-attachments/assets/e53b55cd-a36e-4e4f-8268-bac4bc6de3bf" />

3. In Setup section set Name to "Repurchase Agent" and Descriptiont to "Agent to get prediction about customer repurchase transaction"

<img width="900" height="257" alt="image" src="https://github.com/user-attachments/assets/d958e3cd-cf29-433f-8ce7-eab33ab6f9bd" />

4. Download file named assets/prompt.txt

5. Scroll down to Configuration section --> click Advanced Configuration <img width="161" height="20" alt="image" src="https://github.com/user-attachments/assets/b4dd3001-ed7c-4762-9fc2-7a07ee7dcdd9" /> --> copy content from prompt.txt file that you have downloaded in step 4 and put it here --> click Apply button

<img width="1769" height="888" alt="image" src="https://github.com/user-attachments/assets/d856ba4b-d237-4964-a604-95db356fd374" />

6. Click Save icon <img width="25" height="25" alt="image" src="https://github.com/user-attachments/assets/008cea64-97e9-49b3-920f-616425dbde80" /> --> click Save As --> select Agent as Asset type --> click Save button

<img width="1783" height="900" alt="image" src="https://github.com/user-attachments/assets/851ef9e2-9864-4d83-8990-e4b7a9358d6d" />

7. Ensure that Autosave slider is on <img width="132" height="30" alt="image" src="https://github.com/user-attachments/assets/64effbae-321e-40c4-85de-bad114e826a6" />

## Create Python Function

Overview:
In this section you will create a python function to call API endpoint that you have developed in Lab 03. Below is the process of what you will create:
1. Deploy Python Engine in Deployment Space to be able to create python function
2. Create python function to get customer feature store (that you have created in Lab 02) by Customer ID
3. Create python function to send input payload that contains customer features into Repurchase Model endpoint that you have developed in Lab 03

1. Scroll down to Tools section --> click Create custom tool button

<img width="879" height="118" alt="image" src="https://github.com/user-attachments/assets/a3589add-df98-4bca-a9cf-5f67b3bbb442" />

2. Click Deploy Python Engine 

<img width="1784" height="70" alt="image" src="https://github.com/user-attachments/assets/b6507d46-a63f-48a0-9ef5-c1d4d1555331" />

3. Set Deployment Space to "Repurchase Model Deployment Space" --> click Create button --> after process is completed, close the window

<img width="1778" height="889" alt="image" src="https://github.com/user-attachments/assets/25ce9d22-1c45-47b0-aa29-4d0a465d314a" />

4. Go back to Asset tab --> find cos-connection asset that you have created in Lab 01 and click it

<img width="1567" height="57" alt="image" src="https://github.com/user-attachments/assets/48ac1602-6765-496e-8ae6-fb3fb89122c5" />

5. Here you must copy connection id that can be found in your URL after https://dataplatform.cloud.ibm.com/connections/xxx. xxx is your connection id. in image below, connection id is 019e2aa3-bf42-72a5-a4bc-3349c3ff499c

<img width="1914" height="729" alt="image" src="https://github.com/user-attachments/assets/3942d28d-b161-464e-8886-dd2ff7e98ea4" />

6. Go back to Asset tab and click Repurchase Agent to open it --> click Edit button

<img width="689" height="247" alt="image" src="https://github.com/user-attachments/assets/b9ddcc13-637c-472a-8ba2-c0b5b82c3b1c" />

7. Scroll down to Tools section and click Create Custom Tool button

<img width="877" height="112" alt="image" src="https://github.com/user-attachments/assets/e1e3d7ce-74cd-4074-8331-f5c258dfcc99" />

8. Go to Configure tab --> click Add Secret button <img width="128" height="31" alt="image" src="https://github.com/user-attachments/assets/4108a151-eb46-4480-87ec-c93dd2697f4d" /> --> set Name to "COS_CONNECTION_ID" and Value to connection id that you have copied in step 5 --> click Create Secret button

<img width="1802" height="900" alt="image" src="https://github.com/user-attachments/assets/6a72acd3-d9fc-4e74-95be-b37a51e7aa1d" />

9. Repeat step 8 to add more secrets as below:

* Name: WATSONX_API_KEY; Value: Your API Key that you have created in Lab 01
* Name: WATSONX_URL; Value: https://us-south.ml.cloud.ibm.com --> this is the region where your environment is provisioned
* Name: WATSONX_PROJECT_ID; Value: Get it from your URL using this format: https://dataplatform.cloud.ibm.com/wx/agents/_<agent_id>_?project_id=_<project_id>_&context=wx
* Name: REPURCHASE_MODEL_ENDPOINT; Value: Get it from Lab 03 step 2.10

10. After you setup all secrets you will get picture as below:

<img width="1525" height="406" alt="image" src="https://github.com/user-attachments/assets/97d7e301-7e11-438f-8697-6aa538d4af5c" />

11. Go back to Define tab --> set Name to "Get Customer Feature Values" --> set Description to "Tool to retrieve feature values from the Feature Store table using the provided Customer ID." --> set Input JSON Schema field to `{
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
}`

--> set Python Code field to 
```
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
      bucket_name="repurchasemodel-donotdelete-pr-spincdlcpmf5ao",
      file_name="FEATURE_STORE.csv",
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

12. Go to Test tab --> test if your python code is working by using this payload

```
{
 "customer_id": "1",
 "report_date": "2020-03-31"
}
```

13. Click Run button <img width="87" height="21" alt="image" src="https://github.com/user-attachments/assets/d29e7212-32d6-466c-a581-90d113ede27b" /> --> if you have done correctly you will get result as image below

<img width="875" height="348" alt="image" src="https://github.com/user-attachments/assets/17e34dcd-5bda-42a9-ad9d-06a11264fa87" />

14. Click Save button <img width="62" height="29" alt="image" src="https://github.com/user-attachments/assets/8963521c-7d8d-411f-ac59-0e7fc2120c19" />

15. Test by using this query "get repurchase prediction from customer id 1 as of 31 march 2020". You will see that agent can understand your quey, call tool and respond with human natural language.

<img width="895" height="277" alt="image" src="https://github.com/user-attachments/assets/f692ec6d-ea6a-4ec1-aeaa-9c8cdf80a936" />

16. You can continue to deploy this Agent so 3rd party app may consume as API by clicking Deploy button <img width="107" height="28" alt="image" src="https://github.com/user-attachments/assets/e06a69bc-067f-4a4f-ac49-dfbae2337ce8" /> and follow the follow up steps
