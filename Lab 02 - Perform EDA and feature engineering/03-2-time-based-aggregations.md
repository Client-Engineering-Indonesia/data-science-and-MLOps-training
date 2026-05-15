# Step 3.2: Create Monthly Purchase Transaction Table for Last 3, 6, and 12 Months

[← Previous: Monthly Purchase Table](./03-1-monthly-purchase-table.md) | [Back to Feature Engineering Overview](./03-feature-engineering.md) | [Next: Base User Dataset →](./03-3-base-user-dataset.md)

---

### 3.2 Create Monthly Purchase Transaction Table for Last 3, 6, and 12 Months

**Objective:** Use CUSTOMER_MONTHLY_PURCHASE.csv as the base table to create purchase transaction aggregations for different time periods.

#### 3.2.1 Add Base Data Asset
1. Drag and drop a **Data Asset** node to the canvas
2. Double-click the node
3. Select **Connection**
4. Select **cos-connection**
5. Select your bucket name
6. Select **CUSTOMER_MONTHLY_PURCHASE.csv**
7. Click the **Select** button

<img width="1779" height="894" alt="image" src="https://github.com/user-attachments/assets/36da53f1-63fa-4056-97f2-54ad08ffe113" />

#### 3.2.2 Duplicate Data Asset Node
1. Click the Data Asset node once to select it
2. Copy and paste it in the same canvas
3. You now have 2 Data Asset nodes with the same data source (CUSTOMER_MONTHLY_PURCHASE.csv)

<img width="254" height="384" alt="image" src="https://github.com/user-attachments/assets/887f5f15-74d4-4bc9-96c1-115e20831476" />

#### 3.2.3 Add and Connect Merge Node
1. Find the **Merge** node
2. Drag and drop it to the canvas
3. Draw a line from the first Data Asset to the Merge node
4. Draw a line from the second Data Asset to the Merge node
   - This will join the two data sources

<img width="819" height="353" alt="image" src="https://github.com/user-attachments/assets/0025759a-e2ff-4d98-892e-62271a96e91a" />

#### 3.2.4 Configure Merge Keys
1. Double-click the **Merge** node
2. Under the **Keys** section, check:
   - TOTAL_PURCHASE_AMOUNT_Sum
   - GENDER
   - PURCHASE_PERIOD
3. Click the **Delete** icon: <img width="23" height="27" alt="image" src="https://github.com/user-attachments/assets/b8464df9-dfcc-41df-9144-c023f77b4cc4" />

<img width="627" height="234" alt="image" src="https://github.com/user-attachments/assets/2e6402a2-c223-418a-90d1-a13070018602" />

#### 3.2.5 Configure Filter Settings
Under the **Filter** section, perform the following tasks:

1. **Exclude GENDER from both sources:**
   - Check GENDER from both Data Asset nodes to exclude this field from output

   <img width="865" height="61" alt="image" src="https://github.com/user-attachments/assets/9e20d398-340f-4e24-9be6-124c752dec13" />

2. **Rename PURCHASE_PERIOD from second source:**
   - Change **Output Field** of PURCHASE_PERIOD from second Data Asset node (Tag = 2) to: `PURCHASE_PERIOD_L3M`

   <img width="869" height="40" alt="image" src="https://github.com/user-attachments/assets/1352b7cd-53f0-485d-8a36-22157e6b4551" />

3. **Exclude TOTAL_PURCHASE_AMOUNT from first source:**
   - Check TOTAL_PURCHASE_AMOUNT from first Data Asset node (Tag = 1) to exclude from output

   <img width="869" height="31" alt="image" src="https://github.com/user-attachments/assets/30fbc804-9f65-480c-ac8c-7b7a27b6939c" />

4. **Rename TOTAL_PURCHASE_AMOUNT from second source:**
   - Change **Output Field** of TOTAL_PURCHASE_AMOUNT from second Data Asset node (Tag = 2) to: `TOTAL_PURCHASE_AMOUNT_L3M`

   <img width="867" height="37" alt="image" src="https://github.com/user-attachments/assets/736ba7d3-146d-4211-81f7-c3e58c6aec59" />

5. Click the **Save** button

<img width="890" height="589" alt="image" src="https://github.com/user-attachments/assets/bc991955-30cc-4fa7-9c69-b6470bd92f7b" />

#### 3.2.6 Add Select Node
1. Find the **Select** node
2. Drag and drop it to the canvas
3. Link it with the Merge node

<img width="949" height="372" alt="image" src="https://github.com/user-attachments/assets/27957c6f-b8a1-4163-94ee-6cd40ee6f535" />

#### 3.2.7 Configure Select Condition
1. Double-click the **Select** node
2. Click the **Expression Builder** icon: <img width="25" height="30" alt="image" src="https://github.com/user-attachments/assets/a5b9545d-c4c4-4264-af56-7620a65e0348" /> under **Conditions** section
3. Enter the following expression:
   ```
   date_months_difference(PURCHASE_PERIOD_L3M, PURCHASE_PERIOD) > 0 and date_months_difference(PURCHASE_PERIOD_L3M, PURCHASE_PERIOD) <= 3
   ```
4. Click **Validate** to ensure the formula is correct
5. Click the **OK** button

<img width="1774" height="895" alt="image" src="https://github.com/user-attachments/assets/4c874ac2-27ea-4cd0-83cb-4f7755f91ee0" />

#### 3.2.8 Save Select Configuration
- Click the **Save** button

<img width="475" height="899" alt="image" src="https://github.com/user-attachments/assets/e41dd53c-a9c6-41de-9b27-5dfe9dd2cd21" />

#### 3.2.9 Verify Filtered Data
1. Click the **Preview Data** icon
2. Compare the **PURCHASE_PERIOD** and **PURCHASE_PERIOD_L3M** columns
3. Verify that PURCHASE_PERIOD_L3M values are within the last 3 months relative to PURCHASE_PERIOD

<img width="782" height="712" alt="image" src="https://github.com/user-attachments/assets/f6b25168-b7e6-46fe-b6b8-ff83c16cf1ac" />

#### 3.2.10 Add Aggregate Node
1. Find the **Aggregate** node
2. Drag and drop it to the canvas
3. Link it with the **Select** node

<img width="804" height="348" alt="image" src="https://github.com/user-attachments/assets/da28a6b5-e8ef-49a0-953c-621b73548290" />

#### 3.2.11 Configure Aggregate Keys
1. Double-click the **Aggregate** node
2. Click **Add Columns** under the **Key Fields** section
3. Select **CUSTOMER_ID** and **PURCHASE_PERIOD**
4. Click the **OK** button

<img width="663" height="901" alt="image" src="https://github.com/user-attachments/assets/a49e91c0-e3b9-4b10-bf59-8e1e3a40fcab" />

#### 3.2.12 Set Aggregation Functions
- Under the **Default Mode** section, select:
  - **MEAN**
  - **SUM**
  - **MEDIAN**

<img width="622" height="392" alt="image" src="https://github.com/user-attachments/assets/d3d9acdd-6ab9-432a-a386-b9713805c5ab" />

#### 3.2.13 Add Aggregate Field
1. Click **Add Columns** under the **Aggregate Fields** section
2. Select **TOTAL_PURCHASE_AMOUNT_L3M**
3. Click the **OK** button

<img width="669" height="901" alt="image" src="https://github.com/user-attachments/assets/708e96c0-eb52-490f-bd4f-f78160db99a4" />

#### 3.2.14 Finalize Aggregate Settings
1. Uncheck **Include Record Count**
2. Click the **Save** button

<img width="631" height="633" alt="image" src="https://github.com/user-attachments/assets/6822bd79-c392-4480-b93d-217b73a9294e" />

#### 3.2.15 Verify Aggregated Data
1. Click **Preview Data** on the Aggregate node
2. Verify that data is aggregated for the last 3 months relative to each customer's latest transaction

<img width="1235" height="795" alt="image" src="https://github.com/user-attachments/assets/7ca1889e-328b-4ff5-8df8-f16e74194ea2" />

#### 3.2.16 Add Export Node
1. Find the **Data Asset Export** node
2. Drag and drop it to the canvas
3. Link it with the **Aggregate** node

<img width="1362" height="482" alt="image" src="https://github.com/user-attachments/assets/a1e17370-eb20-484f-ba4b-ee7a715ff359" />

#### 3.2.17 Configure Export Destination
1. Double-click the **Data Asset Export** node
2. Click the **Change Data Asset** button: <img width="207" height="41" alt="image" src="https://github.com/user-attachments/assets/87651182-9568-4d0f-a8f0-d68b60eb6258" />
3. Select **Connection**
4. Select **cos-connection**
5. Select your bucket name
6. In the **New Item** field, enter: `CUSTOMER_PURCHASE_L3M`
7. Click the **Select** button

<img width="1784" height="900" alt="image" src="https://github.com/user-attachments/assets/ccc79c62-f9d4-48c9-a891-a044d8eebbfb" />

#### 3.2.18 Set File Format
1. Change **File Format** to **CSV**
2. Click the **Save** button

<img width="637" height="753" alt="image" src="https://github.com/user-attachments/assets/71a054d1-0794-4435-be1f-ae262c174a69" />

#### 3.2.19 Execute the Flow
1. Click the **Run All** button: <img width="99" height="29" alt="image" src="https://github.com/user-attachments/assets/18040d84-4736-467b-8bc3-8bb88b8dfe2d" />
2. Wait for the process to complete

<img width="1665" height="503" alt="image" src="https://github.com/user-attachments/assets/c2a69dcf-a18e-48c4-a008-4ed9577126e3" />

#### 3.2.20 Verify File Creation
- Once complete, verify that **CUSTOMER_PURCHASE_L3M.csv** appears in your COS bucket
- This file contains 3-month aggregated purchase transactions for each customer

<img width="238" height="39" alt="image" src="https://github.com/user-attachments/assets/56523416-3496-46a1-9a2e-651a7a0f25e9" />

#### 3.2.21 Duplicate Asset for 6-Month Aggregation
1. Return to the **Asset** tab
2. Hover over the **"02.1-Customer Monthly Transaction Last 3 Months"** SPSS Modeler asset
3. Click the **3 dots** icon: <img width="26" height="27" alt="image" src="https://github.com/user-attachments/assets/2ee9918d-ea75-4cbc-b840-f68247effe46" />
4. Select **Duplicate**

<img width="1571" height="366" alt="image" src="https://github.com/user-attachments/assets/3e5b1a54-f605-4bed-ae76-0aef29f384aa" />

#### 3.2.22 Open Duplicated Asset
1. Click the **Refresh** icon after duplication completes
2. Locate **"02.1-Customer Monthly Transaction Last 3 Months copy 1"**
3. Click to open it

<img width="1573" height="161" alt="image" src="https://github.com/user-attachments/assets/7b614eb4-ddac-4d7e-b34d-9efa0120dbb6" />

#### 3.2.23 Rename Asset for 6-Month Period
1. Click the **Flow Information** icon in the top right: <img width="22" height="20" alt="image" src="https://github.com/user-attachments/assets/eed7b55a-777a-4607-aed8-5b697bc98c88" />
2. Change **Name** to: `02.2-Customer Monthly Transaction Last 6 Months`

<img width="320" height="395" alt="image" src="https://github.com/user-attachments/assets/9571b2d6-3080-4665-b50c-e91919ec7fad" />

#### 3.2.24 Update Merge Node for 6 Months
1. Double-click the **Merge** node
2. Change **Output Field** of TOTAL_PURCHASE_AMOUNT_Sum from second Data Asset node (Tag = 2) to: `TOTAL_PURCHASE_AMOUNT_L6M`
3. Change **Output Field** of PURCHASE_PERIOD from second Data Asset node (Tag = 2) to: `PURCHASE_PERIOD_L6M`
4. Click the **Save** button

<img width="1078" height="910" alt="image" src="https://github.com/user-attachments/assets/a5f36534-8247-4cf3-b15d-6492790fd298" />

#### 3.2.25 Update Select Condition for 6 Months
1. Double-click the **Select** node
2. Set **Condition** to:
   ```
   date_months_difference(PURCHASE_PERIOD_L6M, PURCHASE_PERIOD) > 0 and date_months_difference(PURCHASE_PERIOD_L6M, PURCHASE_PERIOD) <= 6
   ```
3. Click the **Save** button

<img width="900" height="909" alt="image" src="https://github.com/user-attachments/assets/c9097ab3-5d35-4520-ae52-3c7f4cc20cdc" />

#### 3.2.26 Update Aggregate Node for 6 Months
1. Double-click the **Aggregate** node
2. Perform the following tasks:

   **a. Remove 3-month field:**
   - Select **TOTAL_PURCHASE_AMOUNT_L3M** and delete it from Aggregate Fields

   <img width="791" height="177" alt="image" src="https://github.com/user-attachments/assets/c9dd2b7f-6d2a-4b40-a6ab-07ef7c90af06" />

   **b. Add 6-month field:**
   - Click **Add Columns** button under Aggregate Fields section
   - Select **TOTAL_PURCHASE_AMOUNT_L6M**
   - Click the **OK** button

   <img width="672" height="901" alt="image" src="https://github.com/user-attachments/assets/2be3110d-a44f-434a-ad40-7d9584fe6984" />

   **c. Finalize settings:**
   - Ensure **Include Record Count** is unchecked
   - Click the **Save** button

<img width="634" height="632" alt="image" src="https://github.com/user-attachments/assets/918f7bed-c08c-4674-9030-a7e7774b814c" />

#### 3.2.27 Update Export File Name
1. Double-click the **Data Asset Export** node
2. Change **File Name** to: `CUSTOMER_PURCHASE_L6M.csv`
3. Click the **Save** button

<img width="1043" height="901" alt="image" src="https://github.com/user-attachments/assets/d5670d98-ccc5-4c91-9f1c-afff81cf35cc" />

#### 3.2.28 Verify 6-Month Data
- Click **Preview Data** on the Aggregate node to verify the data is correct

<img width="1268" height="674" alt="image" src="https://github.com/user-attachments/assets/bd0f7242-12ac-49b4-baca-cf58d28085b0" />

#### 3.2.29 Execute 6-Month Flow
1. Click the **Run All** button: <img width="95" height="27" alt="image" src="https://github.com/user-attachments/assets/6dc2099e-3b56-4c21-9167-faa882f080ae" />
2. Wait for the process to complete

<img width="1640" height="687" alt="image" src="https://github.com/user-attachments/assets/7b2a0a03-395c-416d-96e1-1aa750ace10a" />

#### 3.2.30 Duplicate Asset for 12-Month Aggregation
- Repeat steps 3.2.21 and 3.2.22 to duplicate the asset again

#### 3.2.31 Rename Asset for 12-Month Period
1. Click the **Flow Information** icon in the top right: <img width="22" height="20" alt="image" src="https://github.com/user-attachments/assets/eed7b55a-777a-4607-aed8-5b697bc98c88" />
2. Change **Name** to: `02.3-Customer Monthly Transaction Last 12 Months`

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

---

[← Previous: Monthly Purchase Table](./03-1-monthly-purchase-table.md) | [Back to Feature Engineering Overview](./03-feature-engineering.md) | [Next: Base User Dataset →](./03-3-base-user-dataset.md)
