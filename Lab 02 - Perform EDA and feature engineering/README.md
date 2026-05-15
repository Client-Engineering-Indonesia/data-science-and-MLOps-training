# Perform Exploratory Data Analysis (EDA) and Feature Engineering

Overview:
* In this session, you will use a table that contains individual customer purchase transaction from e-commerce company.
* We will create repurchase model to identify which customers who are most likely to purchase again in next 6 months after they made latest purchase.
* To do this, we will aggregate transactions into monthly basis and use last 12 months to generate customer repurchase probability score (ranging from 0 < score < 1).
* If score is less than or equal to 0.5, the prediction result is "customer will not repurchase in next 6 months"
* If score is greater than 0.5, the prediction result is "customer will repurchase in next 6 months"
* This model will be run on monthly basis on end-of-month

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

Overview:
We will aggregate each purchase transaction into monthly basis to enable the model run every end-of-month.

13. Go back to Asset tab and create new SPSS Modeler asset --> set Name to "01-Customer Monthly Transaction" --> leave Environment Definition as default --> click Create button

<img width="1814" height="879" alt="image" src="https://github.com/user-attachments/assets/56b80c76-4732-488e-9043-73f48e1946c5" />

14. Redo step 3-4

15. Find Derive node --> drag and drop it into right pane --> link it with Data Asset node

<img width="681" height="322" alt="image" src="https://github.com/user-attachments/assets/f6d6cbce-625d-498c-ad4d-c9a3b52e9010" />

Notes: 
Derive node enables you to create new column from existing table

16. Click 2x Derive node --> set Derived Field Name to "PURCHASE_PERIOD"

<img width="477" height="406" alt="image" src="https://github.com/user-attachments/assets/35440103-34b8-4087-98c6-9b76c845efb3" />

17. Click Launch Expression Builder icon <img width="23" height="26" alt="image" src="https://github.com/user-attachments/assets/e3e2188a-9bb0-4b99-8a64-1b1e7d23c261" /> --> set Expression to "date_add_days(-1, date_add_months(1, datetime_date(datetime_year(PURCHASE_DATE), datetime_month(PURCHASE_DATE), 1) ) )" --> click Validate and ensure your formula is correct --> click OK button

<img width="1777" height="894" alt="image" src="https://github.com/user-attachments/assets/a0e649ed-9f57-4968-92a0-120675f02a3f" />

Notes:
For this lab session, we use some functions to convert PURCHASE_DATE to year-and-month-FirstDateOfTheMonth format (YYYY-mm-01). Logic in step 17 will convert purchase transaction date into end of month date. If you have different logic, you can explore other function as well.

18. Click Save button

<img width="475" height="898" alt="image" src="https://github.com/user-attachments/assets/ad189615-c028-4c35-a1cd-b94161ad6f7f" />

19. Hover your mouse to Derive node --> click Preview icon --> here you will see new added column named "PURCHASE_PERIOD"

<img width="1658" height="668" alt="image" src="https://github.com/user-attachments/assets/fdfa4dc7-6909-4622-919f-8deae4c0ad1d" />

20. Find Aggregate node --> drag and drop it to right pane --> link it with Derive node

<img width="929" height="251" alt="image" src="https://github.com/user-attachments/assets/9fb0d5ab-8ff6-4f6c-a600-3db086898034" />

21. Click 2x Aggregate node --> click Add Columns button under Key Fields section

<img width="213" height="115" alt="image" src="https://github.com/user-attachments/assets/996d4d1d-1594-4f06-9ecb-ef6b3f146799" />

22. Select CUSTOMER_ID, GENDER, and PURCHASE_PERIOD --> click OK button

<img width="673" height="905" alt="image" src="https://github.com/user-attachments/assets/18d3f7cc-2606-445c-97e2-1c969bc2d3a5" />

23. Scroll down to Default Mode section --> select SUM

<img width="625" height="388" alt="image" src="https://github.com/user-attachments/assets/d95197eb-79fa-4f70-8168-0ac35a8c1d23" />

24. Scroll up a bit to Aggregate Fields section --> click Add Columns button 

<img width="199" height="110" alt="image" src="https://github.com/user-attachments/assets/702ee163-bf32-4c6b-99cf-c7932d35fb62" />

21. Select TOTAL_PURCHASE_AMOUNT --> click OK button

<img width="671" height="899" alt="image" src="https://github.com/user-attachments/assets/43435b05-9162-47b5-8a7e-2c2785b93adb" />

22. Tick-off Include Record Count --> click Save button

<img width="636" height="899" alt="image" src="https://github.com/user-attachments/assets/e3cadd51-5451-4730-826c-5a160dbb86c4" />

23. Now you will get monthly purchase transaction for each individual customer. You can check how the data looks like by click Preview data. From the image below each transaction has been aggregated to Customer and purchase transaction period (year,month).

<img width="1239" height="644" alt="image" src="https://github.com/user-attachments/assets/12a94603-b0da-4f5b-92db-340ff06a1e05" />

24. Next we are going to export the result into a CSV file stored in cos-connection that we have built previously. To do this, find Data Asset Export node, drag and drop it to right pane, and link it with Aggregate node.

<img width="1141" height="479" alt="image" src="https://github.com/user-attachments/assets/e4e032b0-8780-4713-8dbb-7653ed0c5129" />

25. Click 2x Data Asset Export --> click Change Data Asset button

<img width="632" height="258" alt="image" src="https://github.com/user-attachments/assets/3c656d12-1e6f-463d-adad-cc111526aed7" />

26. Select Connection --> select cos-connection --> select your bucket name (it begins with project name followed with random characters) --> add New Item named "CUSTOMER_MONTHLY_PURCHASE" --> click Select button

<img width="1783" height="900" alt="image" src="https://github.com/user-attachments/assets/9eb31362-87a0-4598-a8c8-dbc3b6e2ea4d" />

27. Change File format to CSV --> ensure First line is header is checked --> click Save button

<img width="634" height="734" alt="image" src="https://github.com/user-attachments/assets/77dfd5d1-b1a5-4109-baef-a37e654312fc" />

28. Now click Run All button <img width="100" height="23" alt="image" src="https://github.com/user-attachments/assets/c700e200-b096-4093-b06f-eefa10b0b2ed" /> --> wait until the process is completed

<img width="1665" height="443" alt="image" src="https://github.com/user-attachments/assets/dd088200-4f41-42cc-829e-1722b56cbf9b" />

29. Once the process is completed, you can see there is new file named "CUSTOMER_MONTHLY_PURCHASE.csv" in your COS bucket.

<img width="1612" height="353" alt="image" src="https://github.com/user-attachments/assets/a94cf5aa-7852-4c08-9100-acfd024718a4" />

Guideline to see all files in your COS bucket:
* Go to IBM Cloud Resource page (https://cloud.ibm.com/resources) --> expand Storage section --> select available Cloud Object Storage instance

<img width="1830" height="88" alt="image" src="https://github.com/user-attachments/assets/a6c605be-3bc4-4a40-8f72-ba6f31f25bec" />

* Here you will see list of existing buckets in Buckets tab --> to know your project bucket name, you must understand this format <YourProjectName>-<RandomCharacters> --> for my case it is "repurchasemodel-donotdelete-pr-spincdlcpmf5ao" with "repurchasemodel" known as my project name and "donotdelete-pr-spincdlcpmf5ao" is random characters generated automatically once you have created watsonx project

<img width="1619" height="412" alt="image" src="https://github.com/user-attachments/assets/832fd5a5-f973-4a17-9fde-2b1c7abf5b43" />

### Create Monthly Purchase Transaction Table in Last 3, 6, and 12 Months


