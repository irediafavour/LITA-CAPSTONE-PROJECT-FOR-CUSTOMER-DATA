# LITA-CAPSTONE-PROJECT-FOR-CUSTOMER-DATA
This document outlines the methodology involved in analyzing customer data to gain valuable insights
## Project Topic: CUSTOMER DATA ANALYSIS PROJECT

[Project Overview](#project-overview)

[Data Source](#data-source)

[Project Objectives](#project-objectives)

[Formula Used](#formula-used)

[Tools Used](#tools-used)

[DATA ANALYSIS](#data-analysis)

[DATA MANIPULATION](#data-manipulation)

[DATA VISUALIZATION AND INFERENCE ](data-visualization-and-inference)

[CONCLUSION](conclusion)

### Project Overview
This project delves into a comprehensive analysis of customer subscription data, sourced from multiple markets and stores within Nigeria's four main regions. By leveraging Microsoft Excel, SQL, and Pivot Tables, I aimed to uncover valuable insights into subscription trends and patterns. The findings were presented in an interactive Power BI dashboard, providing a user-friendly interface for decision-makers to explore the data and make informed strategic choices.

### Data Source
The data for this analysis was sourced from various point-of-sale (POS) systems across the four geopolitical regions in Nigeria: North, East and West. These POS systems track and record customer subscription data, which provides detailed information such as:
* Customer Name: The name of the individual that subscribed
* Subscription Type: The different types of subscription plan
* Subscription start date: The date that the subscription became activated 
* Subscription end date: The date that the subscription became terminated
* Region: The geographical areas (north, south, east and west) where the different stores operate
* Revenue: The money paid for any subscription type

### Project Objectives
This project aims to understand customer behaviour, track subscription types, and identify key trends in cancellations and renewals. 

### Formula Used
1. Average Subscription Type = Datedif(subscription start - subscription end)

### Tools Used
- Microsoft Excel: For analysing the data
- Pivot Table: To organise, summarize and filter the data for easy interpretation
- Structured Query Language: For manipulating 
- Power BI: For creating interactive visualizations and dashboards

## DATA ANALYSIS
This analysis was conducted using Microsoft Excel's PivotTable feature to efficiently summarize and analyze the data. By leveraging PivotTables, I was able to uncover different subscription patterns within the dataset. 
 ### 1. Total count of each subscription type
This analysis calculates the total number of subscriptions for each subscription type, providing insights into the most popular subscription plan.

 ![Total count of each subscription type](https://github.com/user-attachments/assets/0d9dfba6-647e-427c-b223-49b98611f4f0)

 ### 2. Regional Revenue Analysis by Subscription Type
This analysis explores the revenue generated by the different subscription types across the regions. By breaking down the data by region and subscription type, I was able to identify top-performing regions and popular subscription plans.

![Regional revenue analysis by subscription type](https://github.com/user-attachments/assets/9ccdd1ca-5865-462a-ab86-e637eaca0892)

 ### 3. Total count of each subscription type by region
This analysis provides a breakdown of the total count of subscriptions for each type within different regions.

![Total count of subscription type by region](https://github.com/user-attachments/assets/65fec869-dfe0-4022-880d-e60012edc511)

 ### 4. Total count of Cancelled subscription 
This analysis calculates the total number of cancelled subscriptions for each type, where FALSE stands for NO and TRUE stands for YES 

![Cancelled subscription](https://github.com/user-attachments/assets/7be23c06-a06e-47f4-adb6-6de516dc0a90)

## DATA MANIPULATION
This manipulation was conducted using Structured query language to retrieve, group, and delete data within databases using SElECT, GROUP BY, and DELETE statements.
 ### 1. Retrieve the total number of customers from each region
- select Region, count(customerID) as Total_Customers from [dbo].[LITA Capstone Dataset Project (customer data) ]
- Group by Region

![Retrieve the total number of customers from each region](https://github.com/user-attachments/assets/db76c4f8-d7fe-4c2c-bf1e-09b9006f13cf)

 ### 2. Find the most popular subscription type by the number of customers
- SELECT TOP 1 SubscriptionType, COUNT(*) AS Total_Customers FROM [dbo].[LITA Capstone Dataset Project (customer data) ] 
- GROUP BY SubscriptionType

![find the most popular subscription type by the numbers of customers](https://github.com/user-attachments/assets/2b0e61cd-5f35-4b1e-a1a2-1720f8090eeb)

 ### 3. Find customers who cancelled their subscription within 6 months
- select customerID, SubscriptionStart, SubscriptionEnd from [dbo].[LITA Capstone Dataset Project (customer data) ] 
- WHERE DATEDIFF(month, SubscriptionStart, SubscriptionEnd) <= 6

![customers who canceled their subscription within 6 months](https://github.com/user-attachments/assets/3376d8cf-c952-4004-8c6f-7fa07011e03d)

 ### 4. Calculate the average subscription duration for all the customers
- SELECT AVG(DATEDIFF(MONTH, SubscriptionStart, SubscriptionEnd)) AS AverageSubscriptionDuration
- FROM [dbo].[LITA Capstone Dataset Project (customer data) ] 
- WHERE SubscriptionEnd IS NOT NULL

![average subscription duration for all the customers](https://github.com/user-attachments/assets/21985114-5017-40df-919e-0c9294a44283)


 ### 5. Find customers with subscriptions longer than 12 months
- select customerID, SubscriptionStart, SubscriptionEnd from [dbo].[LITA Capstone Dataset Project (customer data) ] 
- WHERE DATEDIFF(month, SubscriptionStart, SubscriptionEnd) > 12

 ![customers with subscriptions longer than 12 months](https://github.com/user-attachments/assets/5f4f6262-a2be-40f4-9ca9-9c995855dc46)

 
 ### 6. Calculate the total revenue by subscription type
- select subscriptiontype, sum (revenue) as total_revenue from [dbo].[LITA Capstone Dataset Project (customer data) ]
- group by subscriptiontype

![total revenue by subscription type](https://github.com/user-attachments/assets/020f8f89-7c40-49a1-9dab-65248c72f240)


 ### 7. Find the top 3 region by subscription cancellations
- SELECT top 3 Region, COUNT(*) AS Cancellation from [dbo].[LITA Capstone Dataset Project (customer data) ]
- WHERE canceled = 1
- GROUP BY Region
- ORDER BY Cancellation DESC

![top 3 region by subscription cancellations](https://github.com/user-attachments/assets/4923cb1f-b620-498b-b031-31a8e58e6b21)

  ### 8. Find the total number of active and cancelled subscriptions
- SELECT COUNT(*) AS TotalSubscriptions,
- SUM(CASE WHEN canceled = 0 THEN 1 ELSE 0 END) AS ActiveSubscriptions,
- SUM(CASE WHEN canceled = 1 THEN 1 ELSE 0 END) AS CanceledSubscriptions
- FROM  [dbo].[LITA Capstone Dataset Project (customer data) ]

![total number of active and canceled subscriptions](https://github.com/user-attachments/assets/cf95f145-c7b8-40ca-940e-a82281cc584c)

## DATA VISUALIZATION
Power BI was used to visualise key customer segments, cancellations, and subscription trends—using slicers for interactive analysis.
This visualization provides a comprehensive overview of key subscription metrics, including revenue, customer count, and subscription type distribution across different regions.

![Customers data](https://github.com/user-attachments/assets/bebf90c5-56d4-4c56-815a-9610a637648b)

![BASIC](https://github.com/user-attachments/assets/617a1e5b-f9ae-4b69-aae3-a1d1a45b1626)

![PREMIUM](https://github.com/user-attachments/assets/2f3f20b3-7038-49f8-a667-6f1c33df33e0)

![STANDARD](https://github.com/user-attachments/assets/feb5a8fd-a5e9-4248-b3d7-0319f5903863)

### Regional Performance:
The use of a slicer was used to show each region's performance
- Total Revenue: The East region generates the highest total revenue

- Customer Count: The East region also has the highest number of customers, which indicates a larger customer base.

- Cancelled Subscription: The North had the highest cancelled subscription

- Active Subscription: The East had the highest active subscription

### Subscription Type Performance: 
The use of a slicer was used to show each subscription types
- Total Revenue: The Basic subscription type generates the highest revenue and is also the top subscription type

- Customer Count: The Basic subscription type has the highest number of customers.

- Cancelled Subscription: The basic subscription was the most cancelled

- Active Subscription: The Basic subscription type was the most active 

## CONCLUSION
By understanding these trends and patterns, businesses can make informed decisions to optimize their subscription strategies, improve customer retention, and drive revenue growth.



