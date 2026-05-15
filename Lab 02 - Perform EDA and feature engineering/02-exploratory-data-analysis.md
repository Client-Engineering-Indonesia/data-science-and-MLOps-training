# Step 2: Perform Exploratory Data Analysis (EDA)

[← Back to Lab 02 Overview](./README.md) | [← Previous: Create SPSS Modeler Asset](./01-create-spss-modeler.md)

---

## 2.1 Add Data Asset Node

1. Locate **Data Asset** under the **Import** section in the left panel
2. Drag and drop it to the canvas (right pane)

<img width="913" height="309" alt="image" src="https://github.com/user-attachments/assets/c115fbfd-9ed6-498c-8793-c4aed7454662" />

## 2.2 Configure Data Source

1. Double-click the **Data Asset** node to open its properties panel
2. Select **Connection**
3. Select **db2-connection**
4. Select **RSH14813** schema
5. Select **CUSTOMER_TRANSACTIONS** table
6. Click the **Select** button

<img width="1773" height="886" alt="image" src="https://github.com/user-attachments/assets/3cf40f51-7ea4-4ea4-8362-f551c2951ed3" />

## 2.3 Save Data Asset Configuration

- In the Data Asset properties panel, click the **Save** button

<img width="642" height="902" alt="image" src="https://github.com/user-attachments/assets/f9f1f014-d2bf-4ab4-a4bf-8bf79cb86a51" />

## 2.4 Preview the Dataset

1. Hover your mouse over the **Data Asset** node
2. Click the **Preview** icon: <img width="1662" height="829" alt="image" src="https://github.com/user-attachments/assets/a10be403-7108-4858-a399-8db3e1817b0b" />
3. Review the displayed dataset

<img width="1662" height="829" alt="image" src="https://github.com/user-attachments/assets/a1292872-b63c-4534-92c7-c5b7374c0304" />

## 2.5 Add Data Audit Node

1. Find the **Data Audit** node in the left panel
2. Drag and drop it to the canvas
3. Hover your mouse over the **Data Asset** node
4. Click and hold the **right arrow** icon: <img width="22" height="19" alt="image" src="https://github.com/user-attachments/assets/65ed57b5-c728-4d04-8c86-98c020f73e10" />
5. Drag to the **Data Audit** node to create a connection

<img width="930" height="373" alt="image" src="https://github.com/user-attachments/assets/85570ea6-8703-429a-b0cc-1909a43ba55e" />

## 2.6 Run Data Audit

- In the **Data Audit** properties panel, click the **Run** button

<img width="481" height="140" alt="image" src="https://github.com/user-attachments/assets/ca7103bb-3fc8-4208-8d85-67f1ace3c169" />

## 2.7 View Audit Results

- In the **Outputs** section, click **Data Audit**

<img width="321" height="223" alt="image" src="https://github.com/user-attachments/assets/185d34a6-14ba-4e69-bf07-09d7eac03144" />

## 2.8 Analyze Data Statistics

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

## 2.9 Explore Individual Columns

1. Click on the **GENDER** column to view its distribution
2. Observe the distribution of MALE and FEMALE values
3. Explore the **Proportion**, **Pareto**, and **Distribution** tabs for additional insights

<img width="1610" height="731" alt="image" src="https://github.com/user-attachments/assets/69dbaac0-eaf2-4448-a395-9597fec0e4f2" />

## 2.10 Analyze Continuous Variables

- Click on **TOTAL_PURCHASE_AMOUNT** to view its analysis
- Note the different analysis options available for continuous data types versus nominal data types

<img width="1605" height="726" alt="image" src="https://github.com/user-attachments/assets/cb5cb00d-eb74-4d63-b638-da8859cc81df" />

---

## Next Steps

Continue to [Step 3: Perform Feature Engineering](./03-feature-engineering.md)