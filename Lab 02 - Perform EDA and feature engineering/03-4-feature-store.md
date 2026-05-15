# Step 3.4: Create Feature Store

[← Previous: Base User Dataset](./03-3-base-user-dataset.md) | [Back to Feature Engineering Overview](./03-feature-engineering.md)

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
2. Set **Join** type to `Partial Outer Join`
3. Verify the configuration matches the image below
4. Click the **Save** button

<img width="577" height="913" alt="image" src="https://github.com/user-attachments/assets/1fb33cc9-cdef-41e2-a62a-426229e5b5b2" />

#### 3.4.8 Add L6M and L12M Data Assets
Repeat steps 3.4.4 through 3.4.7 for:
1. **CUSTOMER_PURCHASE_L6M.csv**
2. **CUSTOMER_PURCHASE_L12M.csv**
3. Ensure you set **Join** type to `Partial Outer Join`

The image below shows the complete end-to-end flow with data preview:

<img width="1127" height="491" alt="image" src="https://github.com/user-attachments/assets/8743aa13-881d-4814-a793-c3ba630b0905" />

#### 3.4.10 Add CUSTOMER_MONTHLY_PURCHASE File
1. Add a **Data Asset** node to the canvas
2. Open Properties panel and click **Change data asset** button <img width="208" height="37" alt="image" src="https://github.com/user-attachments/assets/5e0ad686-9a6c-4949-828f-c50a086d0e70" />
3. Select **Connection**
4. Select **cos-connection**
5. Select your bucket name
6. Select **CUSTOMER_MONTHLY_PURCHASE.csv** file
7. Click **Select** button
8. Click **Save** button

<img width="1595" height="437" alt="image" src="https://github.com/user-attachments/assets/01629ec5-bba5-402f-9e78-4a99adee0b04" />

#### 3.4.11 Join CUSTOMER_MONTHLY_PURCHASE With Latest Data
1. Add a **Merge** node to the canvas
2. Link prior **Merge** node with latest **Merge** node
3. Link **CUSTOMER_MONTHLY_PURCHASE** data asset node with latest **Merge** node

<img width="1048" height="291" alt="image" src="https://github.com/user-attachments/assets/534f7215-9b7d-415a-886c-d942350e96ef" />

#### 3.4.12 Configure GENDER variable
1. Double-click latest **Merge** node
2. Click **Add columns +** button <img width="117" height="30" alt="image" src="https://github.com/user-attachments/assets/bf89c800-d7af-4c60-80b1-8201ed51e0c1" />
3. Select **CUSTOMER_ID** and **PURCHASE_PERIOD**
4. Set **Join** type to `Partial Outer Join`
5. Exclude **TOTAL_PURCHASE_AMOUNT_Sum** from **Filter** section
6. Verify using image below
7. Click **Save** button

<img width="510" height="918" alt="image" src="https://github.com/user-attachments/assets/e9becd21-b896-4ff8-883d-695d561fec9a" />

#### 3.4.13 Export Feature Store
1. Add a **Data Asset Export** node to the canvas
2. Link it to the final Merge node
3. Configure the export:
   - **Connection**: cos-connection
   - **File Name**: `FEATURE_STORE.csv`
   - **File Format**: CSV
4. Click the **Save** button

<img width="574" height="910" alt="image" src="https://github.com/user-attachments/assets/ba5b133d-869c-4a50-b9b3-4f019f6d1eab" />

#### 3.4.14 Execute Feature Store Creation
1. Click the **Run All** button: <img width="87" height="25" alt="image" src="https://github.com/user-attachments/assets/4138fd35-57d5-4f95-9256-1284245653e5" />

<img width="1150" height="307" alt="image" src="https://github.com/user-attachments/assets/ae16f3a3-9c76-409b-bdd4-942ef2a6f78e" />

2. Wait for the process to complete
3. Verify that **FEATURE_STORE.csv** has been created in your COS bucket

<img width="1147" height="52" alt="image" src="https://github.com/user-attachments/assets/771f93dd-5c30-42c9-a7a0-7ec9e615a1ac" />

**Result:** The feature store is now ready to be used as training data for building the repurchase prediction model.


---

[← Previous: Base User Dataset](./03-3-base-user-dataset.md) | [Back to Feature Engineering Overview](./03-feature-engineering.md) | [Next: Lab 03 - Develop and Deploy ML Model →](../Lab%2003%20-%20Develop%20and%20deploy%20ML%20model/README.md)
