<img width="1048" height="291" alt="image" src="https://github.com/user-attachments/assets/534f7215-9b7d-415a-886c-d942350e96ef" />

### 3.4.12 Configure GENDER variable
1. Double-click latest **Merge** node
2. Click **Add columns +** button <img width="117" height="30" alt="image" src="https://github.com/user-attachments/assets/bf89c800-d7af-4c60-80b1-8201ed51e0c1" />
3. Select **CUSTOMER_ID** and **PURCHASE_PERIOD**
4. Set **Join** type to `Partial Outer Join`
5. Exclude **TOTAL_PURCHASE_AMOUNT_Sum** from **Filter** section
6. Verify using image below
7. Click **Save** button

<img width="510" height="918" alt="image" src="https://github.com/user-attachments/assets/e9becd21-b896-4ff8-883d-695d561fec9a" />

### 3.4.13 Export Feature Store
1. Add a **Data Asset Export** node to the canvas
2. Link it to the final Merge node
3. Configure the export:
   - **Connection**: cos-connection
   - **File Name**: `FEATURE_STORE.csv`
   - **File Format**: CSV
4. Click the **Save** button

<img width="574" height="910" alt="image" src="https://github.com/user-attachments/assets/ba5b133d-869c-4a50-b9b3-4f019f6d1eab" />

### 3.4.14 Execute Feature Store Creation
1. Click the **Run All** button: <img width="87" height="25" alt="image" src="https://github.com/user-attachments/assets/4138fd35-57d5-4f95-9256-1284245653e5" />

<img width="1150" height="307" alt="image" src="https://github.com/user-attachments/assets/ae16f3a3-9c76-409b-bdd4-942ef2a6f78e" />

2. Wait for the process to complete
3. Verify that **FEATURE_STORE.csv** has been created in your COS bucket

<img width="1147" height="52" alt="image" src="https://github.com/user-attachments/assets/771f93dd-5c30-42c9-a7a0-7ec9e615a1ac" />

**Result:** The feature store is now ready to be used as training data for building the repurchase prediction model.

---

[← Back to Lab 02 Overview](./README.md) | [Next: Lab 03 - Develop and Deploy ML Model →](../Lab%2003%20-%20Develop%20and%20deploy%20ML%20model/README.md)