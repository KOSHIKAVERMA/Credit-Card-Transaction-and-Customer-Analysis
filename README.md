# Unlocking Insights: Credit Card Transactions and Customer Behavior Analysis
<br>

### PROJECT OVERVIEW

In this project, I uncovered key insights and behavioral patterns in credit card usage using Power BI. I analyzed crucial metrics such as customer age, sexual orientation, marital status, occupation, and education level. By the end, I gained a clearer understanding of how customers use their credit cards, enabling me to predict their needs and provide meaningful insights to the company.

### TABLE OF CONTENTS

- [Problem Statement](#problem-statement)
- [Data Collection](#data-collection)
- [Importing Data](#importing-data)
- [Data Analysis](#data-analysis)
- [Dashboard Preparation](#dashboard-preparation)
- [Insights](#insights)
- [Conclusion](#Conclusion)

  <br>

### PROBLEM STATEMENT

In this project, I analyzed data from a fictional credit card company aiming to understand business performance and customer usage patterns across all **four quarters** of the **2023** financial year. The goal was to identify key trends and highlight areas requiring the most attention to optimize their operations effectively. 

### DATA COLLECTION

The dataset used for this analysis is structured in CSV format and consists of two parts. The first is the **Transaction Dataset**, containing **10,108 rows** and **18 columns**, detailing all customer transactions. Here's a quick glimpse of its contents:

<br>

![Screenshot 2024-10-14 164247](https://github.com/user-attachments/assets/667edfe3-ee42-4427-b01c-8ef4ac904e05)

<br>

**Column Description** :

● **client_Num** : It is the Customer’s transaction number.

● **card_Category** : The type of card that the customer used.

● **Annual_Fees** : The fees that the customer paid for the card annually.

● **Activation_30_Days** : It is the binary indication of whether the customer activated their card within 30 days or not.

● **Customer_Acq_Cost** : The cost incurred to acquire the customer.

● **Week_Start_Date** : It is the date of the first day of each week of the year.

● **Week_Num** : It is the rolling count of the number of weeks.

● **Qtr** : It indicates the quarter of the year.

● **current_year** : It is the operation year.

● **Credit_Limit** : The credit limit assigned to the customer’s card.

● **Total_Revolving_Bal** : The outstanding balance that rolls over from one month to the next.

● **Total_Trans_Amt** : Total amount spent by the customer through their card transactions.

● **Total_Trans_Vol** : Total number of transactions made by the customer using their card.

● **Avg_Utilization_Ratio** : The proportion of revolving credit used relative to the customer’s total available credit.

● **Use_Chip** : The type of payment method the customer used with their card.

● **Exp_Type** : The types of bills the customer paid using their card.

● **Interest_Earned** : The amount of interest the company earned from the customer’s card usage.

● **Delinquent_Acc** : A binary indicator that flags an account if a payment remains overdue for 30 days or more.


 <br> 
 <br> 

The second dataset, the **Customer Dataset**, consists of **10,108 rows** and **15 columns**, containing information on customer demographics, occupations, geographical locations, and other relevant attributes. 

<br>

![Screenshot 2024-10-14 164126](https://github.com/user-attachments/assets/03f9d3f8-7e4b-432d-9ba1-128229c6ceef)

<br>

**Column Description** :

● **Client_Num** : It is the customer’s transaction number.

● **Customer_Age** : Customer’s age.

● **Gender** : Customer’s gender.

● **Dependent_Count** : The number of individuals financially supported by the customer through their card.

● **Education_Level** : The highest level of education that the customer has received.

● **Marital_Status** : Customer’s marital status.

● **state_cd** : Short code of the state that the customer resides in.

● **Zipcode** : The zip code of the place that the customer resides in.

● **Car_Owner** : It indicates whether the customer owns a car or not.

● **House_Owner** : It indicates whether the customer owns a house or not.

● **Personal_loan** : It indicates whether the customer has a personal loan or not.

● **contact** : The type of contact that the customer has provided.

● **Customer_Job** : The job that customer has.

● **Income** : The amount of income the customer earns.

● **Cust_Satisfaction_Score** : The satisfaction score provided by the Customer for the service.

<br>

### DATA MODIFICATION

Before starting the analysis and visualization, I created **additional columns** and **measures** to streamline certain processes. I utilized Power BI's built-in **DAX** tool to develop these enhancements.

#### Added Columns

**1. Revenue**

hdashjhsiahhddddddddddddddddddddddfffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffsjahfusancjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjhuiashkaaaaaaa

``` powerbi
Revenue = credit_card[Annual_Fees] + credit_card[Total_Trans_Amt] + credit_card[Interest_Earned]
```


















