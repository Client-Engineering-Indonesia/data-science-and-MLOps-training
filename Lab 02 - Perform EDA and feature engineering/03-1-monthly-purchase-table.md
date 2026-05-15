# Step 3.1: Create Monthly Purchase Transaction Table

[← Back to Feature Engineering Overview](./03-feature-engineering.md) | [Next: Time-Based Aggregations →](./03-2-time-based-aggregations.md)

---

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

---

---

[← Back to Feature Engineering Overview](./03-feature-engineering.md) | [Next: Time-Based Aggregations →](./03-2-time-based-aggregations.md)
