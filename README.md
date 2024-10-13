# Unlocking Insights: Credit Card Transactions and Customer Behavior Analysis

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
  

### PROBLEM STATEMENT

In this project I have done analysis of a fictional company that provides Credit Card services to the public. The company wants to better understand their business and customer usage trends for all **4 quarters** of the financial year **2022-2023** to streamline and focus on the aspects that needs their most attention. 


### DATA COLLECTION

The dataset used for this analysis is a structured data in CSV format. The Two data Tables are **Transaction Dataset** which contains **10,108 rows** and **18 columns** and has data of all the transactions that the customer placed, a quick look of the data:





Column Description :

● client_Num : It is the client’s transaction number.
● card_Category : It is the type of card that the client used.

● Annual_Fees : It is the fees that the client paid for the card annually.

● Activation_30_Days : It is the binary indication of whether the client activated their card within 30 days or not.

● Customer_Acq_Cost : It is the amunt that went towards acquiring the client.

● Week_Start_Date : It is the date of the first day of each week of the year.

● Week_Num : It is the rolling count of the number of weeks.

● Qtr : It indicates the quarter of the year.

● current_year : It is the operation year.

● Credit_Limit : It is the amount limit of the client’s card.

● Total_Revolving_Bal : It is the balance amount that carries over from one month to the next month.

● Total_Trans_Amt : It is the amount that has been transacted by the client.

● Total_Trans_Vol : It is the number of times that the client has trasacted from their card.

● Avg_Utilization_Ratio : It is the ratio of the amount of revolving credit and the total available credit to the client.

● Use_Chip : It is to indicate what type of method the client used for their card.

● Exp_Type : It is to find out the type of bills that the client used their card for.

● Interest_Earned : It is the amount of interest that the company earned through the client’s card.

● Delinquent_Acc : It is a binary indication that flags an account if a payment if not paid for 30 days or more.



the other one is **Customer Dataset** which contains **10,108 rows** and **15 columns** and has data related to customer demographic, their occuation, geographical location, etc,. 






Column Description :
● Client_Num : It is the client’s transaction number.

● Customer_Age : It is the client’s age.

● Gender : It is the client’s gender.

● Dependent_Count : It is the number of people that the client supports financially with their card.

● Education_Level : It is the highest level of education that the client has received.

● Marital_Status : It is the client’s marital status.

● state_cd : It is the short code of the state that the client resides in.

● Zipcode : It is the zip code of the place that the client resides in.

● Car_Owner : It is the indication to find out if the client owns a car or not.

● House_Owner : It is the indication to find out if the client owns a house or not.

● Personal_loan : It is the indication to find out if the client has personal loan or not.

● contact : It is the type of contact that the client has provided.

● Customer_Job : It is the job that client has.

● Income : It is amount that the client earns.

● Cust_Satisfaction_Score : It is the indication to find out the satisfaction score that the client has provided for the service.


















