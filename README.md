# Unlocking Insights: Credit Card Transactions and Customer Behavior Analysis
<br>

### PROJECT OVERVIEW

In this project, I uncovered key insights and behavioral patterns in credit card usage using Power BI. I analyzed crucial metrics such as customer age, sexual orientation, marital status, occupation, and education level. By the end, I gained a clearer understanding of how customers use their credit cards, enabling me to predict their needs and provide meaningful insights to the company.

### TABLE OF CONTENTS

- [Problem Statement](#problem-statement)
- [Data Collection](#data-collection)
- [Data Cleaning](#data-cleaning)
- [Data Modelling](#data-modelling)
- [Report Building](#report-building)
- [Insights](#insights)
- [Conclusion](#Conclusion)

  <br>

### PROBLEM STATEMENT

In this project, I analyzed data from a fictional credit card company aiming to understand business performance and customer usage patterns across all **four quarters** of the **2023** financial year. The goal was to identify key trends and highlight areas requiring the most attention to optimize their operations effectively. 

### DATA COLLECTION

I found this dataset for this project from kaggle.com. The website has various fictitious datasets for data projects. The dataset used for this analysis is structured in CSV format and consists of two parts. The first is the **Transaction Dataset**, containing **10,108 rows** and **18 columns**, detailing all customer transactions. Here's a quick glimpse of its content:

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

### DATA CLEANING

After importing the files in power BI, I initiated to check for any discripencies in the data. All the **data types** were correct accept for the **date** column so, I changed it to date. 

Then I checked for any **duplicates** or **empty values** using the **column distribution** and **column quality** features in the data preview group, but there were no duplicates and empty values in the data. 


### DATA MODELLING

Before starting the analysis and visualization, I created some **additional columns** and **measures** to streamline certain processes. I utilized Power BI's built-in **DAX** tool to develop these enhancements.

**a) ADDED COLUMNS**

**1. Revenue**

I created a new column to calculate the revenue of customers by adding the annual fees they have paid, the total amount of money generated by their transactions, and the interest earned by the company.

```dax
Revenue = credit_card[Annual_Fees] + credit_card[Total_Trans_Amt] + credit_card[Interest_Earned]
```

**2. Week Number**

I created an additional column to show the weeks by number eg: 1,2,3,etc,.

```dax
Week_num_2 = WEEKNUM( credit_card[Week_Start_Date])
```

**3. Age Group**

I created a column for age group in which I grouped the age of customers in equal age differences to make the analysis more meaningful, the groups included all the ages from 21 to 73  

```dax
Age_Group = SWITCH( 
    true(),
     customer[Customer_Age] < 30, "20-30" ,
     customer[Customer_Age] >= 30 && customer[Customer_Age] < 40, "30-40",
     customer[Customer_Age] >= 40 && customer[Customer_Age] < 50, "40-50",
     customer[Customer_Age] >= 50 && customer[Customer_Age] < 60, "50-60",
     customer[Customer_Age] >= 60, "60+",
      "unknown"
)
```

**4. Income Group**

I created a separate column to group the income in "low", "medium", and "high" income levels to understand customer's credit card' usage trends based on their income levels. 

```dax
Income_Group = SWITCH(
    TRUE(),
    customer[Income] < 35000, "Low",
    customer[Income] >= 35000 && customer[Income] < 70000, "Med",
    customer[Income] >= 70000, "High",
    "unknown"
)
```

<br>

**b) MEASURES**

I developed several key measures to analyze revenue on a **weekly basis**. 

**1. Current_week_revenue**

Current week revenue refers to the **total revenue generated during the most recent or ongoing week**. I calculated the current week's revenue measure using **calculate()** function by **summing** the revenue column and filtering the data using **max()** to only include rows where the week number matches the maximum week number to calculate the most recent week's revenue.  

```dax
Current_week_Revenue = CALCULATE(
    SUM( credit_card[Revenue]), 
    FILTER(
        ALL(credit_card),
        credit_card[Week_num_2] = MAX(credit_card[Week_num_2])))
```

**2. Previous_week_revenue**

Previous week revenue refers to the **total revenue generated during the week immediately before the current one**. It helps in comparing performance week-over-week.
The only change in this formula is the filter condition. I have **subtracted 1 from the max()** function to target the previous week’s data. This ensured the calculation reflected revenue from the week immediately before the current one.

```dax
Previous_week_Revenue = CALCULATE(
    SUM( credit_card[Revenue]), 
    FILTER(
        ALL(credit_card),
        credit_card[Week_num_2] = MAX(credit_card[Week_num_2])-1))
```

**3. WOW_Revenue**

Week-on-week (WoW) revenue measures the **change in revenue from one week to the next**. It shows the **difference in earnings compared to the previous week**. I calculated the week on week revenue by dividing the current week' revenue by the previous week's revenue. 

```dax
WOW_Revenue = DIVIDE(([Current_week_Revenue] - [Previous_week_Revenue]), [Previous_week_Revenue])
```
<br>

### REPORT BUILDING

I divided the visualization into two sections: one focuses on a detailed analysis of all **transactions**, and the other provides insights into the company’s **customers**.

#### TRANSACTION ANALYSIS

- **KPIs**:

**Revenue (57M)** – Displays the total revenue generated.

**Total Interest (8M)** – The cumulative interest earned from all customers.

**Amount (46M)** – Sum of all transaction amounts.

**Count (656K)** – Total number of transactions conducted.

<br>

- **Matrix (Card Category Breakdown)**:

-Provides a summary of revenue, transaction amounts, and interest earned by card type (Blue, Gold, Platinum, Silver).

**Insight**: The Blue card contributes the highest revenue and transaction volume.

<br>

- **Bar and Combo Charts**:
  
**1. Quarterly Revenue & Transaction Volume (Q1-Q4)**

- **Combo Chart**: Shows both the sum of revenue (bars) and total transaction volume (line) per quarter.
  
- **Insight**: Revenue peaks in Q4, with a slight drop in transaction volume towards the end.
  
**2. Revenue by Expenditure Type**

- Top categories include Bills, Entertainment, and Fuel.
  
- **Insight**: Bills contribute the highest revenue, indicating regular usage for utilities and essentials.
  
**3. Revenue by Education Level**

- Graduate-level customers generate the most revenue.
  
- **Insight**: Education level correlates with higher spending.
  
**4. Revenue by Customer Job**

- Business professionals account for the largest revenue share.
  
- **Insight**: Professionals are the primary revenue drivers, followed by white-collar employees.
  
**5. Revenue by Use Chip**

- Swipe transactions generate the highest revenue, followed by chip and online transactions.
 
- **Insight**: Customers primarily prefer in-person payments over online methods.
  
**6. Revenue by Card Category**

The Blue card leads in revenue, reinforcing its popularity among customers.

<br>

#### CUSTOMER ANALYSIS


