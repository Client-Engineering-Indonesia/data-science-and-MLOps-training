# Perform Exploratory Data Analysis (EDA) and Feature Engineering

Overview

In this session, you will use a table that contains individual customer purchase transaction from e-commerce company. Then we will create repurchase model to identify which customers who are most likely to purchase again in next 6 months after they made latest purchase.

## Create SPSS Modeler Asset

1. In Asset tab, click New Asset button --> type "SPSS" in search field --> select "Build models as a visual flow"

<img width="1788" height="507" alt="image" src="https://github.com/user-attachments/assets/70fc3e20-3e50-4895-9a3a-9aaf2010c762" />

2. Set Name to "00-Exploratory Data Analysis" --> set Environment Definition to "Default SPSS Modeler S (2 vCPU 8 GB RAM)" --> click Create button

<img width="1808" height="883" alt="image" src="https://github.com/user-attachments/assets/30d9fdc5-6fae-4bc5-89aa-8c087c330d78" />

## Perform Exploratory Data Analysis (EDA)

3. Select Data Asset under Import section, drag and drop it to right pane 

<img width="913" height="309" alt="image" src="https://github.com/user-attachments/assets/c115fbfd-9ed6-498c-8793-c4aed7454662" />

4. Click it 2x to open Data Asset panel --> select Connection --> select db2-connection --> select RSH14813 --> select CUSTOMER_TRANSACTIONS table --> click Select button

<img width="1773" height="886" alt="image" src="https://github.com/user-attachments/assets/3cf40f51-7ea4-4ea4-8362-f551c2951ed3" />

5. In Data Asset properties panel, click Save button

<img width="642" height="902" alt="image" src="https://github.com/user-attachments/assets/f9f1f014-d2bf-4ab4-a4bf-8bf79cb86a51" />

6. Hover your mouse to Data Asset node --> click Preview icon <img width="1662" height="829" alt="image" src="https://github.com/user-attachments/assets/a10be403-7108-4858-a399-8db3e1817b0b" /> --> it will display existing dataset

<img width="1662" height="829" alt="image" src="https://github.com/user-attachments/assets/a1292872-b63c-4534-92c7-c5b7374c0304" />

7. Find Data Audit node and put it ob right pane --> hover your mouse in Data Asset node --> click and hold right arrow icon <img width="22" height="19" alt="image" src="https://github.com/user-attachments/assets/65ed57b5-c728-4d04-8c86-98c020f73e10" /> --> move your mouse to Data Audit node to link Data Asset with this new Data Audit

<img width="930" height="373" alt="image" src="https://github.com/user-attachments/assets/85570ea6-8703-429a-b0cc-1909a43ba55e" />

8. In Data Audit properties panel, click Run button

<img width="481" height="140" alt="image" src="https://github.com/user-attachments/assets/ca7103bb-3fc8-4208-8d85-67f1ace3c169" />

9. In Outputs section click Data Audit

<img width="321" height="223" alt="image" src="https://github.com/user-attachments/assets/185d34a6-14ba-4e69-bf07-09d7eac03144" />

10. Here you will see basic statistics from the data. For example data type, min, max, mean, standard deviation, and unique value from each column

<img width="1793" height="615" alt="image" src="https://github.com/user-attachments/assets/28cc0162-aa57-459e-a907-166e63525808" />

Notes:
For training purposes, we will focus on several columns as below:
* CUSTOMER_ID: unique customer identifier
* PURCHASE_DATE: when customer made purchase transaction
* TOTAL_PURCHASE_AMOUNT: total purchase amount
* GENDER: customer gender

11. You can start exploring each column above by clicking it. Let's start by clicking GENDER. Here you will distribution of each gender (MALE and FEMALE). You can go to Proportion, Pareto, and Distribution to see other analysis. 

<img width="1610" height="731" alt="image" src="https://github.com/user-attachments/assets/69dbaac0-eaf2-4448-a395-9597fec0e4f2" />

12. Now take a look at TOTAL_PURCHASE_AMOUNT. Here you will difference analysis based on its data type (Continuous or Nominal).

<img width="1605" height="726" alt="image" src="https://github.com/user-attachments/assets/cb5cb00d-eb74-4d63-b638-da8859cc81df" />

## Perform Feature Engineering

### Create Monthly Purchase Transaction Table

13. Go back to Asset tab and create new SPSS Modeler asset --> set Name to "01-Customer Monthly Transaction" --> leave Environment Definition as default --> click Create button

<img width="1814" height="879" alt="image" src="https://github.com/user-attachments/assets/56b80c76-4732-488e-9043-73f48e1946c5" />

14. Redo step 3-4

15. Find Derive node --> drag and drop it into right pane --> link it with Data Asset node

<img width="681" height="322" alt="image" src="https://github.com/user-attachments/assets/f6d6cbce-625d-498c-ad4d-c9a3b52e9010" />

Notes: 
Derive node enables you to create new column from existing table

16. Click 2x Derive node --> set Derived Field Name to "PURCHASE_PERIOD"

<img width="477" height="406" alt="image" src="https://github.com/user-attachments/assets/35440103-34b8-4087-98c6-9b76c845efb3" />

17. Click Launch Expression Builder icon <img width="23" height="26" alt="image" src="https://github.com/user-attachments/assets/e3e2188a-9bb0-4b99-8a64-1b1e7d23c261" /> --> set Expression to "datetime_year(PURCHASE_DATE) >< "-" >< datetime_month(PURCHASE_DATE)" --> click Validate and ensure your formula is correct --> click OK button

<img width="1776" height="900" alt="image" src="https://github.com/user-attachments/assets/fa1553ee-ab2d-4e25-afc5-bde08334f869" />

Notes:
For this lab session, we use some functions to convert PURCHASE_DATE to year-and-month format (YYYY-mm). If you have different logic, you can explore other function as well.

18. Click Save button

<img width="470" height="322" alt="image" src="https://github.com/user-attachments/assets/285a7cf9-aaec-417d-84ee-43091cf4b7be" />

14. Redo step 3-4 --> find Aggregate node --> drag and drop it into right pane --> link Data Asset node with Aggregate node

<img width="748" height="331" alt="image" src="https://github.com/user-attachments/assets/6706d80a-a8e2-46a4-8d92-16eb3265bcd4" />

15. Hover your mouse to Derive node --> click Preview icon --> here you will see new added column named "PURCHASE_PERIOD"

<img width="1653" height="671" alt="image" src="https://github.com/user-attachments/assets/74fa3c12-d3c9-48a8-af21-b8fb411437df" />

16. Find Aggregate node --> drag and drop it to right pane --> link it with Derive node

<img width="948" height="237" alt="image" src="https://github.com/user-attachments/assets/09ea59c1-cece-44d3-b097-0eae4b8c307b" />

17. Click Add Columns button under Key Fields section

<img width="222" height="112" alt="image" src="https://github.com/user-attachments/assets/5a6f08dc-5bbb-4dd6-afe2-a8e55798292b" />

18. Select CUSTOMER_ID and PURCHASE_PERIOD --> click OK button

<img width="665" height="583" alt="image" src="https://github.com/user-attachments/assets/106d10de-95e1-42e7-bcb5-ce5d3b5f64fa" />

19. Click Add Columns button under Aggregate Fields section

<img width="213" height="116" alt="image" src="https://github.com/user-attachments/assets/c9bfb57a-3330-41a3-9cfa-01ae03349a5e" />

20. Select TOTAL_PURCHASE_AMOUNT --> click OK button

<img width="678" height="863" alt="image" src="https://github.com/user-attachments/assets/9801b450-e1f0-425b-941d-75e4207a3a30" />

21. Select MEAN, SUM, MIN, MAX, MEDIAN under Default Mode section

<img width="628" height="390" alt="image" src="https://github.com/user-attachments/assets/a18ba6a6-582a-44d7-9fe6-4e2d6acddae2" />

22. Tick-off Include Record Count --> click Save button

<img width="639" height="594" alt="image" src="https://github.com/user-attachments/assets/e88d6d62-9f84-4dda-924e-ab04bcd6fa66" />

23. 
