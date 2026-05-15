# Step 3.3: Create Base User Dataset

[← Previous: Time-Based Aggregations](./03-2-time-based-aggregations.md) | [Back to Feature Engineering Overview](./03-feature-engineering.md) | [Next: Feature Store →](./03-4-feature-store.md)

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

[← Previous: Time-Based Aggregations](./03-2-time-based-aggregations.md) | [Back to Feature Engineering Overview](./03-feature-engineering.md) | [Next: Feature Store →](./03-4-feature-store.md)
