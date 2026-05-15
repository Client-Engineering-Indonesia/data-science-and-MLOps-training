# Lab 02: Perform Exploratory Data Analysis (EDA) and Feature Engineering

## Overview

In this lab, you will:
* Work with customer purchase transaction data from an e-commerce company
* Create a repurchase prediction model to identify customers likely to purchase again within the next 6 months
* Aggregate transactions on a monthly basis using the last 12 months of data
* Generate customer repurchase probability scores (ranging from 0 to 1)
  - **Score ≤ 0.5**: Customer will NOT repurchase in the next 6 months
  - **Score > 0.5**: Customer WILL repurchase in the next 6 months
* Run the model monthly at end-of-month

---

## Step 1: Create SPSS Modeler Asset

### 1.1 Create New SPSS Modeler Flow
1. Navigate to the **Asset** tab
2. Click the **New Asset** button
3. Type "SPSS" in the search field
4. Select **"Build models as a visual flow"**

<img width="1788" height="507" alt="image" src="https://github.com/user-attachments/assets/70fc3e20-3e50-4895-9a3a-9aaf2010c762" />

### 1.2 Configure SPSS Modeler Settings
1. Set **Name** to: `00-Exploratory Data Analysis`
2. Set **Environment Definition** to: `Default SPSS Modeler S (2 vCPU 8 GB RAM)`
3. Click the **Create** button

<img width="1808" height="883" alt="image" src="https://github.com/user-attachments/assets/30d9fdc5-6fae-4bc5-89aa-8c087c330d78" />

---

## Step 2: Perform Exploratory Data Analysis (EDA)

### 2.1 Add Data Asset Node
1. Locate **Data Asset** under the **Import** section in the left panel
2. Drag and drop it to the canvas (right pane)

<img width="913" height="309" alt="image" src="https://github.com/user-attachments/assets/c115fbfd-9ed6-498c-8793-c4aed7454662" />

### 2.2 Configure Data Source
1. Double-click the **Data Asset** node to open its properties panel
2. Select **Connection**
3. Select **db2-connection**
4. Select **RSH14813** schema
5. Select **CUSTOMER_TRANSACTIONS** table
6. Click the **Select** button

<img width="1773" height="886" alt="image" src="https://github.com/user-attachments/assets/3cf40f51-7ea4-4ea4-8362-f551c2951ed3" />

### 2.3 Save Data Asset Configuration
- In the Data Asset properties panel, click the **Save** button

<img width="642" height="902" alt="image" src="https://github.com/user-attachments/assets/f9f1f014-d2bf-4ab4-a4bf-8bf79cb86a51" />

### 2.4 Preview the Dataset
1. Hover your mouse over the **Data Asset** node
2. Click the **Preview** icon: <img width="1662" height="829" alt="image" src="https://github.com/user-attachments/assets/a10be403-7108-4858-a399-8db3e1817b0b" />
3. Review the displayed dataset

<img width="1662" height="829" alt="image" src="https://github.com/user-attachments/assets/a1292872-b63c-4534-92c7-c5b7374c0304" />

### 2.5 Add Data Audit Node
1. Find the **Data Audit** node in the left panel
2. Drag and drop it to the canvas
3. Hover your mouse over the **Data Asset** node
4. Click and hold the **right arrow** icon: <img width="22" height="19" alt="image" src="https://github.com/user-attachments/assets/65ed57b5-c728-4d04-8c86-98c020f73e10" />
5. Drag to the **Data Audit** node to create a connection

<img width="930" height="373" alt="image" src="https://github.com/user-attachments/assets/85570ea6-8703-429a-b0cc-1909a43ba55e" />

### 2.6 Run Data Audit
- In the **Data Audit** properties panel, click the **Run** button

<img width="481" height="140" alt="image" src="https://github.com/user-attachments/assets/ca7103bb-3fc8-4208-8d85-67f1ace3c169" />

### 2.7 View Audit Results
- In the **Outputs** section, click **Data Audit**

<img width="321" height="223" alt="image" src="https://github.com/user-attachments/assets/185d34a6-14ba-4e69-bf07-09d7eac03144" />

### 2.8 Analyze Data Statistics
Review the basic statistics displayed for each column:
- Data type
- Minimum and maximum values
- Mean and standard deviation
- Unique value counts

<img width="1793" height="615" alt="image" src="https://github.com/user-attachments/assets/28cc0162-aa57-459e-a907-166e63525808" />

**Key Columns for This Lab:**
- **CUSTOMER_ID**: Unique customer identifier
- **PURCHASE_DATE**: Transaction date
- **TOTAL_PURCHASE_AMOUNT**: Total purchase amount
- **GENDER**: Customer gender

### 2.9 Explore Individual Columns
1. Click on the **GENDER** column to view its distribution
2. Observe the distribution of MALE and FEMALE values
3. Explore the **Proportion**, **Pareto**, and **Distribution** tabs for additional insights

<img width="1610" height="731" alt="image" src="https://github.com/user-attachments/assets/69dbaac0-eaf2-4448-a395-9597fec0e4f2" />

### 2.10 Analyze Continuous Variables
- Click on **TOTAL_PURCHASE_AMOUNT** to view its analysis
- Note the different analysis options available for continuous data types versus nominal data types

<img width="1605" height="726" alt="image" src="https://github.com/user-attachments/assets/cb5cb00d-eb74-4d63-b638-da8859cc81df" />

---

## Step 3: Perform Feature Engineering

### 3.1 Create Monthly Purchase Transaction Table

**Objective:** Aggregate purchase transactions on a monthly basis to enable end-of-month model execution.

#### 3.1.1 Create New SPSS Modeler Asset
1. Return to the **Asset** tab
2. Create a new **SPSS Modeler** asset
3. Set **Name** to: `01-Customer Monthly Transaction`
4. Leave **Environment Definition** as default
5. Click the **Create** button

<img width="1814" height="879" alt="image" src="https://github.com/user-attachments/assets/56b80c76-4732-488e-9043-73f48e1946c5" />

#### 3.1.2 Add and Configure Data Asset
- Repeat steps 2.1 and 2.2 to add and configure the Data Asset node

#### 3.1.3 Add Derive Node
1. Find the **Derive** node in the left panel
2. Drag and drop it to the canvas
3. Link it with the **Data Asset** node

<img width="681" height="322" alt="image" src="https://github.com/user-attachments/assets/f6d6cbce-625d-498c-ad4d-c9a3b52e9010" />

> **Note:** The Derive node allows you to create new columns from existing table data.

#### 3.1.4 Configure Derived Field
1. Double-click the **Derive** node
2. Set **Derived Field Name** to: `PURCHASE_PERIOD`

<img width="477" height="406" alt="image" src="https://github.com/user-attachments/assets/35440103-34b8-4087-98c6-9b76c845efb3" />

#### 3.1.5 Create Expression for Purchase Period
1. Click the **Launch Expression Builder** icon: <img width="23" height="26" alt="image" src="https://github.com/user-attachments/assets/e3e2188a-9bb0-4b99-8a64-1b1e7d23c261" />
2. Enter the following expression:
   ```
   date_add_days(-1, date_add_months(1, datetime_date(datetime_year(PURCHASE_DATE), datetime_month(PURCHASE_DATE), 1)))
   ```
3. Click **Validate** to ensure the formula is correct
4. Click the **OK** button

<img width="1777" height="894" alt="image" src="https://github.com/user-attachments/assets/a0e649ed-9f57-4968-92a0-120675f02a3f" />

> **Note:** This expression converts the PURCHASE_DATE to the last day of the month (end-of-month date). You can explore other functions if you have different logic requirements.

#### 3.1.6 Save Derive Configuration
- Click the **Save** button

<img width="475" height="898" alt="image" src="https://github.com/user-attachments/assets/ad189615-c028-4c35-a1cd-b94161ad6f7f" />

#### 3.1.7 Preview Derived Column
1. Hover your mouse over the **Derive** node
2. Click the **Preview** icon
3. Verify the new **PURCHASE_PERIOD** column has been added

<img width="1658" height="668" alt="image" src="https://github.com/user-attachments/assets/fdfa4dc7-6909-4622-919f-8deae4c0ad1d" />

#### 3.1.8 Add Aggregate Node
1. Find the **Aggregate** node in the left panel
2. Drag and drop it to the canvas
3. Link it with the **Derive** node

<img width="929" height="251" alt="image" src="https://github.com/user-attachments/assets/9fb0d5ab-8ff6-4f6c-a600-3db086898034" />

#### 3.1.9 Configure Key Fields
1. Double-click the **Aggregate** node
2. Click the **Add Columns** button under the **Key Fields** section

<img width="213" height="115" alt="image" src="https://github.com/user-attachments/assets/996d4d1d-1594-4f06-9ecb-ef6b3f146799" />

#### 3.1.10 Select Key Columns
1. Select **CUSTOMER_ID**, **GENDER**, and **PURCHASE_PERIOD**
2. Click the **OK** button

<img width="673" height="905" alt="image" src="https://github.com/user-attachments/assets/18d3f7cc-2606-445c-97e2-1c969bc2d3a5" />

#### 3.1.11 Set Aggregation Mode
1. Scroll down to the **Default Mode** section
2. Select **SUM**

<img width="625" height="388" alt="image" src="https://github.com/user-attachments/assets/d95197eb-79fa-4f70-8168-0ac35a8c1d23" />

#### 3.1.12 Add Aggregate Fields
1. Scroll up to the **Aggregate Fields** section
2. Click the **Add Columns** button

<img width="199" height="110" alt="image" src="https://github.com/user-attachments/assets/702ee163-bf32-4c6b-99cf-c7932d35fb62" />

#### 3.1.13 Select Amount Field
1. Select **TOTAL_PURCHASE_AMOUNT**
2. Click the **OK** button

<img width="671" height="899" alt="image" src="https://github.com/user-attachments/assets/43435b05-9162-47b5-8a7e-2c2785b93adb" />

#### 3.1.14 Finalize Aggregate Settings
1. Uncheck **Include Record Count**
2. Click the **Save** button

<img width="636" height="899" alt="image" src="https://github.com/user-attachments/assets/e3cadd51-5451-4730-826c-5a160dbb86c4" />

#### 3.1.15 Verify Aggregated Data
1. Click **Preview Data** on the Aggregate node
2. Verify that transactions are now aggregated by customer and purchase period (year, month)

<img width="1239" height="644" alt="image" src="https://github.com/user-attachments/assets/12a94603-b0da-4f5b-92db-340ff06a1e05" />

#### 3.1.16 Add Data Export Node
1. Find the **Data Asset Export** node
2. Drag and drop it to the canvas
3. Link it with the **Aggregate** node

<img width="1141" height="479" alt="image" src="https://github.com/user-attachments/assets/e4e032b0-8780-4713-8dbb-7653ed0c5129" />

#### 3.1.17 Configure Export Settings
1. Double-click the **Data Asset Export** node
2. Click the **Change Data Asset** button

<img width="632" height="258" alt="image" src="https://github.com/user-attachments/assets/3c656d12-1e6f-463d-adad-cc111526aed7" />

#### 3.1.18 Set Export Destination
1. Select **Connection**
2. Select **cos-connection**
3. Select your bucket name (format: `<ProjectName>-<RandomCharacters>`)
4. In the **New Item** field, enter: `CUSTOMER_MONTHLY_PURCHASE`
5. Click the **Select** button

<img width="1783" height="900" alt="image" src="https://github.com/user-attachments/assets/9eb31362-87a0-4598-a8c8-dbc3b6e2ea4d" />

#### 3.1.19 Set File Format
1. Change **File format** to **CSV**
2. Ensure **First line is header** is checked
3. Click the **Save** button

<img width="634" height="734" alt="image" src="https://github.com/user-attachments/assets/77dfd5d1-b1a5-4109-baef-a37e654312fc" />

#### 3.1.20 Execute the Flow
1. Click the **Run All** button: <img width="100" height="23" alt="image" src="https://github.com/user-attachments/assets/c700e200-b096-4093-b06f-eefa10b0b2ed" />
2. Wait for the process to complete

<img width="1665" height="443" alt="image" src="https://github.com/user-attachments/assets/dd088200-4f41-42cc-829e-1722b56cbf9b" />

#### 3.1.21 Verify File Creation
- Once complete, verify that **CUSTOMER_MONTHLY_PURCHASE.csv** appears in your COS bucket

<img width="1612" height="353" alt="image" src="https://github.com/user-attachments/assets/a94cf5aa-7852-4c08-9100-acfd024718a4" />

**How to View Files in Your COS Bucket:**

1. Navigate to IBM Cloud Resource page: https://cloud.ibm.com/resources
2. Expand the **Storage** section
3. Select your **Cloud Object Storage** instance

<img width="1830" height="88" alt="image" src="https://github.com/user-attachments/assets/a6c605be-3bc4-4a40-8f72-ba6f31f25bec" />

4. Go to the **Buckets** tab to view all buckets
5. Locate your project bucket using the format: `<YourProjectName>-<RandomCharacters>`
   - Example: `repurchasemodel-donotdelete-pr-spincdlcpmf5ao`
   - "repurchasemodel" = project name
   - "donotdelete-pr-spincdlcpmf5ao" = auto-generated characters

<img width="1619" height="412" alt="image" src="https://github.com/user-attachments/assets/832fd5a5-f973-4a17-9fde-2b1c7abf5b43" />

### Create Monthly Purchase Transaction Table in Last 3, 6, and 12 Months

Notes:
Now we are going to use CUSTOMER_MONTHLY_PURCHASE.csv as our base table to create purchase transaction aggregation.

30. Drag and drop Data Asset node into right pane --> click 2x --> then select Connection --> select cos-connection --> select your bucket name --> select CUSTOMER_MONTHLY_PURCHASE.csv --> click Select Button

<img width="1779" height="894" alt="image" src="https://github.com/user-attachments/assets/36da53f1-63fa-4056-97f2-54ad08ffe113" />

31. Click it 1x --> copy it and paste in the same pane --> you will have 2 Data Asset node with same data source which is CUSTOMER_MONTHLY_PURCHASE.csv

<img width="254" height="384" alt="image" src="https://github.com/user-attachments/assets/887f5f15-74d4-4bc9-96c1-115e20831476" />

32. Find Merge node --> drag and drop it to right pane --> draw line from first Data Asset to Merge node --> draw second Data Asset to Merge node --> here we are going to join these 2 data sources

<img width="819" height="353" alt="image" src="https://github.com/user-attachments/assets/0025759a-e2ff-4d98-892e-62271a96e91a" />

33. Click 2x Merge node --> tick-on TOTAL_PURCHASE_AMOUNT_Sum, GENDER, and PURCHASE_PERIOD under Keys section --> click Delete icon <img width="23" height="27" alt="image" src="https://github.com/user-attachments/assets/b8464df9-dfcc-41df-9144-c023f77b4cc4" />

<img width="627" height="234" alt="image" src="https://github.com/user-attachments/assets/2e6402a2-c223-418a-90d1-a13070018602" />

34. Under Filter section, do these tasks:

* Tick-on GENDER from both Data Source node to exclude this field when processing the output

<img width="865" height="61" alt="image" src="https://github.com/user-attachments/assets/9e20d398-340f-4e24-9be6-124c752dec13" />

* Change Output Field of PURCHASE_PERIOD from second Data Asset node (Tag = 2) to "PURCHASE_PERIOD_L3M"

<img width="869" height="40" alt="image" src="https://github.com/user-attachments/assets/1352b7cd-53f0-485d-8a36-22157e6b4551" />

* Tick-on TOTAL_PURCHASE_ANOUNT from first Data Asset node (Tag = 1) to exclude this field when processing the output

<img width="869" height="31" alt="image" src="https://github.com/user-attachments/assets/30fbc804-9f65-480c-ac8c-7b7a27b6939c" />

* Change Outpul Field of TOTAL_PURCHASE_ANOUNT from second Data Asset node (Tag = 2) to "TOTAL_PURCHASE_AMOUNT_L3M"

<img width="867" height="37" alt="image" src="https://github.com/user-attachments/assets/736ba7d3-146d-4211-81f7-c3e58c6aec59" />

* Click Save button

<img width="890" height="589" alt="image" src="https://github.com/user-attachments/assets/bc991955-30cc-4fa7-9c69-b6470bd92f7b" />

35. Find Select node --> drag and drop it to right pane

<img width="949" height="372" alt="image" src="https://github.com/user-attachments/assets/27957c6f-b8a1-4163-94ee-6cd40ee6f535" />

36. Click 2x Select node --> Click Expression Builder icon <img width="25" height="30" alt="image" src="https://github.com/user-attachments/assets/a5b9545d-c4c4-4264-af56-7620a65e0348" /> under Conditions section --> type "date_months_difference(PURCHASE_PERIOD_L3M, PURCHASE_PERIOD) > 0 and date_months_difference(PURCHASE_PERIOD_L3M, PURCHASE_PERIOD) <= 3" to Expression field --> click Validate to ensure your formula is correct --> click OK button

<img width="1774" height="895" alt="image" src="https://github.com/user-attachments/assets/4c874ac2-27ea-4cd0-83cb-4f7755f91ee0" />

37. Click Save button

<img width="475" height="899" alt="image" src="https://github.com/user-attachments/assets/e41dd53c-a9c6-41de-9b27-5dfe9dd2cd21" />

38. Click Preview Data icon --> look at column PURCHASE_PERIOD and PURCHASE_PERIOD_L3M --> you will see that values from PURCHASE_PERIOD_L3M is less than or equal to PURCHASE_PERIOD --> here we have filtered the data into last 3 months by referring to customer latest purchase transaction

<img width="782" height="712" alt="image" src="https://github.com/user-attachments/assets/f6b25168-b7e6-46fe-b6b8-ff83c16cf1ac" />

39. Find Aggregate node and put it into right pane --> link it with Select node

<img width="804" height="348" alt="image" src="https://github.com/user-attachments/assets/da28a6b5-e8ef-49a0-953c-621b73548290" />

40. Click 2x Aggregate node --> click Add Columns under Key Fields section --> select CUSTOMER_ID and PURCHASE_PERIOD --> click OK button

<img width="663" height="901" alt="image" src="https://github.com/user-attachments/assets/a49e91c0-e3b9-4b10-bf59-8e1e3a40fcab" />

41. Select MEAN, SUM, and MEDIAN under Default Mode section

<img width="622" height="392" alt="image" src="https://github.com/user-attachments/assets/d3d9acdd-6ab9-432a-a386-b9713805c5ab" />

42. Click Add Columns under Aggregate Fields section --> select TOTAL_PURCHASE_AMOUNT_L3M --> click OK button

<img width="669" height="901" alt="image" src="https://github.com/user-attachments/assets/708e96c0-eb52-490f-bd4f-f78160db99a4" />

43. Tick off Include Record Cound --> click Save button

<img width="631" height="633" alt="image" src="https://github.com/user-attachments/assets/6822bd79-c392-4480-b93d-217b73a9294e" />

44. Click Preview Data on Aggregate node to see latest data --> you will find that the data is aggregated into last 3 months compared with customer latest transaction on monthly basis

<img width="1235" height="795" alt="image" src="https://github.com/user-attachments/assets/7ca1889e-328b-4ff5-8df8-f16e74194ea2" />

45. Find Data Asset Export node and put it into right pane --> link it with Aggregate node

<img width="1362" height="482" alt="image" src="https://github.com/user-attachments/assets/a1e17370-eb20-484f-ba4b-ee7a715ff359" />

46. Click 2x Data Asset Export node --> select Change Data Asset button <img width="207" height="41" alt="image" src="https://github.com/user-attachments/assets/87651182-9568-4d0f-a8f0-d68b60eb6258" /> --> select Connection --> select cos-connection --> select your bucket name --> on New Item field, type "CUSTOMER_PURCHASE_L3M" --> click Save button

<img width="1784" height="900" alt="image" src="https://github.com/user-attachments/assets/ccc79c62-f9d4-48c9-a891-a044d8eebbfb" />

47. Change File Format to CSV --> click Save button

<img width="637" height="753" alt="image" src="https://github.com/user-attachments/assets/71a054d1-0794-4435-be1f-ae262c174a69" />

48. Click Run All button <img width="99" height="29" alt="image" src="https://github.com/user-attachments/assets/18040d84-4736-467b-8bc3-8bb88b8dfe2d" /> and wait the process completed 

<img width="1665" height="503" alt="image" src="https://github.com/user-attachments/assets/c2a69dcf-a18e-48c4-a008-4ed9577126e3" />

49. Once the process completed, you will see CUSTOMER_PURCHASE_L3M.csv in your COS bucket. This file is aggregated 3 months purchase transaction for each individual customer.

<img width="238" height="39" alt="image" src="https://github.com/user-attachments/assets/56523416-3496-46a1-9a2e-651a7a0f25e9" />

50. Go back to Asset tab --> hover your mouse to "02.1-Customer Monthly Transaction Last 3 Months" SPSS Modeler asset --> click 3 dots icon <img width="26" height="27" alt="image" src="https://github.com/user-attachments/assets/2ee9918d-ea75-4cbc-b840-f68247effe46" /> --> select Duplicate

<img width="1571" height="366" alt="image" src="https://github.com/user-attachments/assets/3e5b1a54-f605-4bed-ae76-0aef29f384aa" />

51. Click Refresh icon once asset is successfully duplicated --> you will see "02.1-Customer Monthly Transaction Last 3 Months copy 1" in your view --> click it

<img width="1573" height="161" alt="image" src="https://github.com/user-attachments/assets/7b614eb4-ddac-4d7e-b34d-9efa0120dbb6" />

52. Now we want to create customer purchase transaction in last 6 months. First change this asset name by clicking Flow Information icon in top right side <img width="22" height="20" alt="image" src="https://github.com/user-attachments/assets/eed7b55a-777a-4607-aed8-5b697bc98c88" /> --> change Name to "02.2-Customer Monthly Transaction Last 6 Months"

<img width="320" height="395" alt="image" src="https://github.com/user-attachments/assets/9571b2d6-3080-4665-b50c-e91919ec7fad" />

53. Click 2x Merge node --> change Output Field of TOTAL_PURCHASE_AMOUNT_Sum from second Data Asset node (Tag = 2) to "TOTAL_PURCHASE_AMOUNT_L6M" --> change Output Field of PURCHASE_PERIOD from second Data Asset node (Tag = 2) to "PURCHASE_PERIOD_L6M" --> click Save button

<img width="1078" height="910" alt="image" src="https://github.com/user-attachments/assets/a5f36534-8247-4cf3-b15d-6492790fd298" />

54. Click 2x Select node --> set Condition to "date_months_difference(PURCHASE_PERIOD_L6M, PURCHASE_PERIOD) > 0 and date_months_difference(PURCHASE_PERIOD_L6M, PURCHASE_PERIOD) <= 6" --> click Save button

<img width="900" height="909" alt="image" src="https://github.com/user-attachments/assets/c9097ab3-5d35-4520-ae52-3c7f4cc20cdc" />

55. Click 2x Aggregate node and do several tasks as below:

* Select TOTAL_PURCHASE_AMOUNT_L3M and delete it from Aggregate Fields

<img width="791" height="177" alt="image" src="https://github.com/user-attachments/assets/c9dd2b7f-6d2a-4b40-a6ab-07ef7c90af06" />

* Click Add Columns button under Aggregate Fields section --> select TOTAL_PURCHASE_AMOUNT_L6M --> select OK button

<img width="672" height="901" alt="image" src="https://github.com/user-attachments/assets/2be3110d-a44f-434a-ad40-7d9584fe6984" />

* Ensure Include Record Count is unchecked --> click Save button

<img width="634" height="632" alt="image" src="https://github.com/user-attachments/assets/918f7bed-c08c-4674-9030-a7e7774b814c" />

56. Click 2x Data Asset Export node --> change File Name to CUSTOMER_PURCHASE_L6M.csv --> click Save button

<img width="1043" height="901" alt="image" src="https://github.com/user-attachments/assets/d5670d98-ccc5-4c91-9f1c-afff81cf35cc" />

57. Click Preview Data icon in Aggregate node to ensure the data is as expected

<img width="1268" height="674" alt="image" src="https://github.com/user-attachments/assets/bd0f7242-12ac-49b4-baca-cf58d28085b0" />

57. Click Run All button <img width="95" height="27" alt="image" src="https://github.com/user-attachments/assets/6dc2099e-3b56-4c21-9167-faa882f080ae" /> and wait until process completed

<img width="1640" height="687" alt="image" src="https://github.com/user-attachments/assets/7b2a0a03-395c-416d-96e1-1aa750ace10a" />

58. Redo step 50-51

59. Now we want to create customer purchase transaction in last 12 months. First change this asset name by clicking Flow Information icon in top right side <img width="22" height="20" alt="image" src="https://github.com/user-attachments/assets/eed7b55a-777a-4607-aed8-5b697bc98c88" /> --> change Name to "02.3-Customer Monthly Transaction Last 12 Months"

<img width="319" height="407" alt="image" src="https://github.com/user-attachments/assets/ce0473d6-9770-4d8c-bacd-a805e5c386a5" />

#### 3.2.32 Update Merge Node for 12 Months
1. Double-click the **Merge** node
2. Change **Output Field** of TOTAL_PURCHASE_AMOUNT_Sum from second Data Asset node (Tag = 2) to: `TOTAL_PURCHASE_AMOUNT_L12M`
3. Change **Output Field** of PURCHASE_PERIOD from second Data Asset node (Tag = 2) to: `PURCHASE_PERIOD_L12M`
4. Click the **Save** button

<img width="1063" height="901" alt="image" src="https://github.com/user-attachments/assets/27775e36-e0ec-43e4-b8af-5693b7201dbd" />

#### 3.2.33 Update Select Condition for 12 Months
1. Double-click the **Select** node
2. Set **Condition** to:
   ```
   date_months_difference(PURCHASE_PERIOD_L12M, PURCHASE_PERIOD) > 0 and date_months_difference(PURCHASE_PERIOD_L12M, PURCHASE_PERIOD) <= 12
   ```
3. Click the **Save** button

<img width="903" height="909" alt="image" src="https://github.com/user-attachments/assets/9b647651-8201-4b04-87d9-724e4b91ef01" />

#### 3.2.34 Update Aggregate Node for 12 Months
1. Double-click the **Aggregate** node
2. Perform the following tasks:

   **a. Remove 3-month field:**
   - Select **TOTAL_PURCHASE_AMOUNT_L3M** and delete it from Aggregate Fields

   <img width="791" height="177" alt="image" src="https://github.com/user-attachments/assets/c9dd2b7f-6d2a-4b40-a6ab-07ef7c90af06" />

   **b. Add 12-month field:**
   - Click **Add Columns** button under Aggregate Fields section
   - Select **TOTAL_PURCHASE_AMOUNT_L12M**
   - Click the **OK** button

   <img width="670" height="901" alt="image" src="https://github.com/user-attachments/assets/77d0041c-ec3f-43a8-b5a4-3b9d795a94fe" />

   **c. Finalize settings:**
   - Ensure **Include Record Count** is unchecked
   - Click the **Save** button

<img width="634" height="632" alt="image" src="https://github.com/user-attachments/assets/918f7bed-c08c-4674-9030-a7e7774b814c" />

#### 3.2.35 Update Export File Name
1. Double-click the **Data Asset Export** node
2. Change **File Name** to: `CUSTOMER_PURCHASE_L12M.csv`
3. Click the **Save** button

<img width="897" height="916" alt="image" src="https://github.com/user-attachments/assets/ca3fc6a8-db84-474e-a8e7-db48351a8b05" />

#### 3.2.36 Verify 12-Month Data
- Click **Preview Data** on the Aggregate node to verify the data is correct

<img width="1257" height="642" alt="image" src="https://github.com/user-attachments/assets/f9403d8a-b73b-4c0f-851f-0641315e37b6" />

#### 3.2.37 Execute 12-Month Flow
1. Click the **Run All** button: <img width="95" height="27" alt="image" src="https://github.com/user-attachments/assets/6dc2099e-3b56-4c21-9167-faa882f080ae" />
2. Wait for the process to complete

---

### 3.3 Create Base User Dataset

**Objective:** Create a ground truth dataset for repurchase activity. This dataset will include customer data with their actual purchase behavior in the next 6 months.

**Labels:**
- **"N"**: Customer did NOT repurchase in the next 6 months
- **"Y"**: Customer DID repurchase in the next 6 months

#### 3.3.1 Create New SPSS Modeler Asset
1. Go to the **Asset** tab
2. Create a new **SPSS Modeler** asset
3. Set **Name** to: `03-Create Base User`
4. Click the **Create** button

<img width="1814" height="882" alt="image" src="https://github.com/user-attachments/assets/20010827-09f8-429a-a133-60559a2e53d8" />

#### 3.3.2 Add Data Asset
1. Drag and drop a **Data Asset** node to the canvas
2. Double-click the node
3. Select **Connection**
4. Select **cos-connection**
5. Select your bucket name
6. Select **CUSTOMER_MONTHLY_PURCHASE.csv**
7. Click the **Select** button

<img width="1779" height="894" alt="image" src="https://github.com/user-attachments/assets/36da53f1-63fa-4056-97f2-54ad08ffe113" />

#### 3.3.3 Add Sort Node
1. Find the **Sort** node
2. Drag and drop it to the canvas
3. Link it with the **Data Asset** node

<img width="706" height="329" alt="image" src="https://github.com/user-attachments/assets/638122a2-116e-49b4-b9c9-663f1991c311" />

#### 3.3.4 Configure Sort Columns
1. Double-click the **Sort** node
2. Click the **Add Columns** button: <img width="127" height="33" alt="image" src="https://github.com/user-attachments/assets/34cc7124-2ee1-4138-902f-45641fa51cbb" />
3. Select **CUSTOMER_ID** and **PURCHASE_PERIOD**
4. Click the **Save** button

<img width="482" height="901" alt="image" src="https://github.com/user-attachments/assets/09c9d0ce-5622-4afb-aaf7-98c7e5097e31" />

#### 3.3.5 Add History Node
1. Find the **History** node
2. Drag and drop it to the canvas
3. Link it with the **Sort** node

<img width="885" height="218" alt="image" src="https://github.com/user-attachments/assets/636caa4c-627a-4749-96ac-a815d0eab567" />

#### 3.3.6 Configure History Node
1. Double-click the **History** node
2. Click the **Add Columns** button: <img width="119" height="29" alt="image" src="https://github.com/user-attachments/assets/bbd82fe6-ec7e-4ca9-9a31-2149b8f9b66d" /> under **Selected Fields** section
3. Select **CUSTOMER_ID** and **PURCHASE_PERIOD**
4. Set **Offset** to: `1`
5. Set **Span** to: `1`
6. Click the **Save** button

<img width="479" height="907" alt="image" src="https://github.com/user-attachments/assets/4baf6cfb-813f-4d57-9b3a-b4441c26132c" />

#### 3.3.7 Verify History Output
1. Click the **Preview Data** icon on the History node
2. Observe the **PURCHASE_PERIOD_1** column, which contains the prior purchase transaction date

<img width="1078" height="422" alt="image" src="https://github.com/user-attachments/assets/0a588083-cbd2-4144-88dd-2b9832427e7a" />

#### 3.3.8 Add Select Node to Filter Same Customer
1. Find the **Select** node
2. Drag and drop it to the canvas
3. Link it with the **History** node
4. Double-click the **Select** node
5. In the Expression Builder, enter: `CUSTOMER_ID = CUSTOMER_ID__1`
6. Click the **Save** button

<img width="714" height="757" alt="image" src="https://github.com/user-attachments/assets/95b80f12-cc0a-41c8-a089-fd56d1427fc3" />

> **Note:** The History node relies on data order, so we need to exclude prior transactions with different CUSTOMER_ID values.

<img width="478" height="905" alt="image" src="https://github.com/user-attachments/assets/840f1714-23ce-4c99-b737-30050df7a0fb" />

#### 3.3.9 Add Derive Node for Repurchase Label
1. Find the **Derive** node
2. Drag and drop it to the canvas
3. Link it with the **Select** node
4. Double-click the **Derive** node
5. Set **Derived Field Name** to: `REPURCHASE`
6. In the Expression Builder, enter:
   ```
   if date_months_difference(PURCHASE_PERIOD__1, PURCHASE_PERIOD) > 0 and date_months_difference(PURCHASE_PERIOD__1, PURCHASE_PERIOD) <= 6 then "Y" else "N" endif
   ```
7. Click the **Save** button

<img width="483" height="906" alt="image" src="https://github.com/user-attachments/assets/9ba2c122-7efd-4047-95b7-8a70cb95b15e" />

#### 3.3.10 Add Filter Node to Standardize Columns
1. Find the **Filter** node
2. Drag and drop it to the canvas
3. Link it with the **Derive** node
4. Double-click the **Filter** node
5. Perform the following tasks:
   - **Filter out** (exclude) these fields:
     - TOTAL_PURCHASE_AMOUNT_Sum
     - GENDER
     - PURCHASE_PERIOD
     - CUSTOMER_ID__1
   - **Rename** PURCHASE_PERIOD__1 to: `PURCHASE_PERIOD`
6. Click the **Save** button

<img width="964" height="862" alt="image" src="https://github.com/user-attachments/assets/12aacde4-22f4-4abe-bc63-00940f67bd6c" />

#### 3.3.11 Verify Filtered Data
- Click the **Preview Data** icon on the Filter node to review the final dataset structure

<img width="594" height="650" alt="image" src="https://github.com/user-attachments/assets/02849627-85a7-40bb-af2f-282586336ace" />

#### 3.3.12 Add Export Node
1. Find the **Data Asset Export** node
2. Drag and drop it to the canvas
3. Link it with the **Filter** node
4. Double-click the **Data Asset Export** node
5. Click the **Change Data Asset** button
6. Select **Connection**
7. Select **cos-connection**
8. Select your bucket name
9. In the **New Item** field, enter: `BASE_USER`
10. Click the **Select** button

<img width="1773" height="897" alt="image" src="https://github.com/user-attachments/assets/d3948096-e59d-410e-9624-eb98d3c8f2b0" />

#### 3.3.13 Set File Format
1. Change **File Format** to **CSV**
2. Click the **Save** button

<img width="625" height="470" alt="image" src="https://github.com/user-attachments/assets/d9fa3f33-0e9f-4ad5-950c-d9b3ed7b527e" />

#### 3.3.14 Execute the Flow
1. Click the **Run All** button: <img width="99" height="29" alt="image" src="https://github.com/user-attachments/assets/90ac25bf-17a4-479b-a75c-3609883edf7e" />
2. Wait for BASE_USER.csv to be generated

<img width="1666" height="402" alt="image" src="https://github.com/user-attachments/assets/14762ab8-212a-4dd8-bd7e-701b28e43d62" />

---

### 3.4 Create Feature Store

**Objective:** Build a feature store containing all attributes needed for machine learning model development. This will combine features from the 3, 6, and 12-month aggregated tables.

#### 3.4.1 Create New SPSS Modeler Asset
1. Go to the **Asset** tab
2. Create a new **SPSS Modeler** asset
3. Set **Name** to: `04-Create Feature Store`
4. Click the **Create** button

<img width="1823" height="895" alt="image" src="https://github.com/user-attachments/assets/ad5fa62e-92f5-4b80-b4e4-6d328f524655" />

#### 3.4.2 Add BASE_USER Data Asset
1. Drag and drop a **Data Asset** node to the canvas
2. Double-click the node
3. Select **Connection**
4. Select **cos-connection**
5. Select your bucket name
6. Select **BASE_USER.csv**
7. Click the **Select** button

<img width="1771" height="897" alt="image" src="https://github.com/user-attachments/assets/49b083e6-4a38-4c41-b8be-459d32425d01" />

#### 3.4.3 Save BASE_USER Configuration
- Click the **Save** button

#### 3.4.4 Add L3M Data Asset
1. Drag and drop another **Data Asset** node to the canvas
2. Double-click the node
3. Select **Connection**
4. Select **cos-connection**
5. Select your bucket name
6. Select **CUSTOMER_PURCHASE_L3M.csv**
7. Click the **Select** button

<img width="1778" height="899" alt="image" src="https://github.com/user-attachments/assets/e274d075-fea7-4139-9c6e-33bcf1e896cd" />

#### 3.4.5 Save L3M Configuration
- Click the **Save** button

#### 3.4.6 Add Merge Node for L3M
1. Drag and drop a **Merge** node to the canvas
2. Link the **BASE_USER** Data Asset node to the Merge node (first connection)
3. Link the **CUSTOMER_PURCHASE_L3M** Data Asset node to the Merge node (second connection)

<img width="806" height="428" alt="image" src="https://github.com/user-attachments/assets/dba54406-464c-4be0-9523-aeb8c0be6f51" />

#### 3.4.7 Configure L3M Merge
1. Double-click the **Merge** node
2. Verify the configuration matches the image below
3. Click the **Save** button

<img width="577" height="907" alt="image" src="https://github.com/user-attachments/assets/4a470ed4-4f05-425f-a3a7-65d02269f813" />

#### 3.4.8 Add L6M and L12M Data Assets
Repeat steps 3.4.4 through 3.4.7 for:
1. **CUSTOMER_PURCHASE_L6M.csv**
2. **CUSTOMER_PURCHASE_L12M.csv**

The image below shows the complete end-to-end flow with data preview:

<img width="1530" height="714" alt="image" src="https://github.com/user-attachments/assets/33d4ced1-73b2-43b7-94b5-ddcea263e4a9" />

#### 3.4.9 Export Feature Store
1. Add a **Data Asset Export** node to the canvas
2. Link it to the final Merge node
3. Configure the export:
   - **Connection**: cos-connection
   - **File Name**: `FEATURE_STORE.csv`
   - **File Format**: CSV
4. Click the **Save** button

<img width="574" height="910" alt="image" src="https://github.com/user-attachments/assets/ba5b133d-869c-4a50-b9b3-4f019f6d1eab" />

#### 3.4.10 Execute Feature Store Creation
1. Click the **Run All** button: <img width="87" height="25" alt="image" src="https://github.com/user-attachments/assets/4138fd35-57d5-4f95-9256-1284245653e5" />
2. Wait for the process to complete
3. Verify that **FEATURE_STORE.csv** has been created in your COS bucket

**Result:** The feature store is now ready to be used as training data for building the repurchase prediction model.

<img width="1147" height="52" alt="image" src="https://github.com/user-attachments/assets/771f93dd-5c30-42c9-a7a0-7ec9e615a1ac" />


