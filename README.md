Descriptive Analysis of Delayed Payments Impacting Cash Flow

Project Title

Understanding Delayed Payment Patterns in the Finance Department

Objective

To identify patterns and root causes of late payments by analyzing financial transaction data, derive actionable insights to mitigate delays, and improve organizational cash flow management.

Dataset

Payment Records: PaymentID, CustomerID, InvoiceID, PaymentDate, DueDate, Amount, Status

Invoice Details: InvoiceID, CustomerID, InvoiceDate, Amount

Customer Profiles: CustomerID, Name, Contact Info, Payment Behavior

Methodology

Data Collection and Preparation

A structured data lake was implemented on AWS S3, organizing raw source files into appropriately named buckets and folders. AWS Glue was used to crawl and catalog datasets, enabling schema inference and metadata enrichment. Data cleaning steps included:

Missing Value Handling: Imputation of missing dates and amounts, or removal of irreparable records.

Data Type Standardization: Ensuring date formats are consistent (YYYY-MM-DD) and monetary values use uniform decimal precision.

Duplicate Removal: Identifying and dropping records with identical keys to avoid skewing analyses.

Normalization: Splitting data into fact and dimension tables to reduce redundancy and support relational joins.

•	Business problem analysis (Fishbone diagram)
![image](https://github.com/user-attachments/assets/d762cc49-72c7-4af9-a709-44db79babf3d)
Figure 1: Fishbone design
Business Problem Analysis

A Fishbone  diagram was constructed to categorize potential delay factors (e.g., process inefficiencies, customer policies, system constraints, human errors). This analysis guided subsequent feature engineering and hypothesis testing.
•	Dataset schema and design planning
![image](https://github.com/user-attachments/assets/a885de25-ed84-4dbd-b1c3-4b9c1156bca4)

 

Figure 2: Business question analysis
![image](https://github.com/user-attachments/assets/43c56753-254c-4d87-b5a9-16fce801185f)

 

Figure 3: Data lake design on excel
•	Data lake setup (buckets, folders, region, tags)
![image](https://github.com/user-attachments/assets/a011af2f-82df-4d60-a607-bac1349b4476)

 
Figure 4: Data lake design on draw.io
Data Lake & Infrastructure Design

•	The AWS environment was secured and scaled using:

VPC Configuration: Private subnets for EC2 and Glue endpoints to isolate traffic.

EC2 Instances: Provisioned for custom ETL and ad-hoc analysis workloads.

Security Groups: Fine-grained ingress/egress rules limiting access to trusted IP ranges and service endpoints.

•	Infrastructure setup (VPC, EC2, Security Group)
![image](https://github.com/user-attachments/assets/12cf26be-c94a-423f-bd4d-a2ff2b4a42b7)
Figure 5: VPC created
![image](https://github.com/user-attachments/assets/464ad178-f7f5-413f-9d0e-1771897e1531)
Figure 6: Security group created
![image](https://github.com/user-attachments/assets/5a8a7ddb-ffff-4b8f-995f-43615d552f0f)

 

Figure 7: Instances created

•	Documentation of data sources and structure
•	Launch and Run virtual Server
![image](https://github.com/user-attachments/assets/b0cec7d5-aa81-47e8-99cd-1247618ad548)

 

Figure 8: Documentation of data sources 

Descriptive Statistics

Cost Evaluation of Ingestion

Using the AWS Pricing Calculator, storage and request costs were estimated based on S3 usage tiers and Glue Data Catalog transactions. This analysis ensured budget alignment and identified cost-optimization opportunities in data partitioning.
![image](https://github.com/user-attachments/assets/0fdbf4f3-9ed1-4f86-8269-28a0e1051bed)

 

Figure 9: Cost Evaluation of Dataset Ingestion


•	Dataset Cleaning Analysis and Design

For each table, DataBrew recipes were drafted to document transformation steps. Metrics such as record counts pre- and post-cleaning, null value percentages, and data quality scores were tracked.
![image](https://github.com/user-attachments/assets/7f96e6c6-eddf-4ebd-9666-c063c1212cf3)
Figure 10: Dataset Cleaning Analysis & Design for Payment records
![image](https://github.com/user-attachments/assets/0d050cbb-8713-43c3-bc54-d0ff230ff858)

 
Figure 11: Dataset Cleaning Analysis & Design for Invoice details
![image](https://github.com/user-attachments/assets/4db01e31-b7d0-4689-bc4d-dc8b4896720d)


 
Figure 12: Dataset Cleaning Analysis & Design for Customer Profiles


•	Dataset Cleaning Implementation
DataBrew jobs executed transformations at scale, with logs forwarded to CloudWatch. Each recipe was version-controlled to support reproducibility.


![image](https://github.com/user-attachments/assets/cddc3fd0-793e-438c-b2a3-7853cfdddcd7)

 
Figure 13: Dataset Cleaning Implementation on DataBrew
![image](https://github.com/user-attachments/assets/ebdc3709-41aa-4c42-b507-e3b797fa54a9)

 
Figure 14: Dataset Cleaning Implementation for payment record on system
![image](https://github.com/user-attachments/assets/12a8a652-f4f4-4867-879f-5c964a18f4a0)

 

Figure 15: Dataset Cleaning Implementation for payment record on User
![image](https://github.com/user-attachments/assets/ad331082-ec74-4265-8441-648c7eef551d)


 
Figure 16: Dataset Cleaning Implementation for invoice details on system
![image](https://github.com/user-attachments/assets/faa57e50-b0cb-4b38-94de-72e04820d534)


 
Figure 17: Dataset Cleaning Implementation for invoice details on user

3.	Data Visualization:
Profiling & ETL Design

Initial profiling uncovered distribution of payment delays and correlations with invoice terms. ETL workflows were sketched in Excel and refined using AWS Glue and Lambda functions for orchestration.
•	Cost Evaluation of Dataset Profiling and Cleaning
![image](https://github.com/user-attachments/assets/b9e6eab1-7eb7-4a94-9fee-6ac1be782747)

 
Figure 18: Cost Evaluation of Dataset Profiling and Cleaning



![image](https://github.com/user-attachments/assets/94b740f8-7bbe-4893-8df7-d9c673821de0)

 
Figure 19: ETL Analysis on Excel
![image](https://github.com/user-attachments/assets/2df5891e-137d-47c7-b366-bae5812cf0fd)

 
Figure 20: Data Enriching on Excel
![image](https://github.com/user-attachments/assets/ec799cb8-77d2-445d-83b3-b9f2dcc650da)



 
Figure 21: Data Summarization on Excel
![image](https://github.com/user-attachments/assets/9ba5c297-3d9e-4a19-8c54-2b2a06c33465)


 
Figure 22: ETL Design


•	•	ETL Implementation

Glue jobs and Lambda triggers automated data movement from raw to curated zones. CloudWatch alarms notified on job failures and SLA breaches.

![image](https://github.com/user-attachments/assets/59d4b65a-8c7d-4a83-81bb-c897df9b7bf2)


Figure 23: Alarms created using Cloudwatch
![image](https://github.com/user-attachments/assets/f6080faa-b8c0-4e75-845c-edcf3a8cc56f)



 
Figure 24: ETL Implementation curator bucket on system
![image](https://github.com/user-attachments/assets/98eb016d-20cb-4baf-9966-ee352cb6fcd1)


 
Figure 25: ETL Implementation curator bucket on user
![image](https://github.com/user-attachments/assets/25d62581-f88d-45f1-8367-2b214eac5c7e)


 
Figure 26: Data Catalog 
![image](https://github.com/user-attachments/assets/a2d384c1-b891-491c-845a-4d72ed545703)

 

Figure 27: Data enriching
![image](https://github.com/user-attachments/assets/a0c63886-9b10-4e70-a78f-5f8894e9288d)

 
Figure 28: Data summarization
![image](https://github.com/user-attachments/assets/30dee312-51bd-4695-a599-f709570c88ae)

 
Figure 29: Data summarization result




4.	Customer Segmentation 
•	Grouped customers based on payment behavior using AWS Glue Data Brew.
•	Segmented them into:
High Risk: >50% delayed payments or avg. delay >15 days
Medium Risk: 20–50% delayed payments
Low Risk: <20% delayed payments

5.	Insights and Findings 
•	Peak delays occurred at month-end 
•	Shorter invoice terms (Net-15) had fewer delays than longer ones (Net-30/45). 
•	Digital payments had better on-time rates; delays were common with manual methods.
6.	Recommendations 
•	Set up auto-reminders before due dates for high-risk clients.
•	Revise terms for frequent defaulters (e.g., switch from Net-30 to Net-15).
•	Encourage digital payments with small incentives.
•	Use dashboards to monitor delay trends and high-risk accounts.
•	Enforce late fee policies for repeated delays.


Tools and Technologies
•	Data Analysis: AWS Glue DataBrew, Excel, Pandas
•	Visualization: Tableau / Power BI
•	Storage & Compute: AWS S3, EC2, VPC
•	Cost Analysis: AWS Pricing Calculator

Deliverables
•	Cleaned datasets and structured data lake
•	Cost analysis and ETL design documents
•	Visual dashboard (delays, trends, risk zones)
•	Summary report and stakeholder-ready presentation





AWS Deployment and Service Models 
•	Objective
To understand AWS cloud deployment (public, private, hybrid, multi cloud) and service models (IaaS, PaaS, SaaS). The difference between the traditional computing model and the cloud computing model as per their location, access, and privacy.
•	Tools and Services Used
AWS Management Console and draw.io.
![image](https://github.com/user-attachments/assets/86264cab-0473-40e9-8bd8-aa72819ff743)


 
 
Figure 30: Traditional computing model VS Cloud computing model
![image](https://github.com/user-attachments/assets/b948aded-c4e0-4034-b803-b097834b412f)




Figure 31: Case study 2_Cloud Deployment Models
![image](https://github.com/user-attachments/assets/a7774040-3813-423a-b4c8-f52546b89a89)



 
Figure 32: Case study 2_Diferrence between Public, Private, Hybrid, and Multi cloud
![image](https://github.com/user-attachments/assets/a3d4e9f9-9576-4d3f-ab11-45370f523ef6)





Figure 33: Case Study 3_Cloud Service Models
![image](https://github.com/user-attachments/assets/9a9e5520-6e6c-49e4-9282-54fd4eae4c08)



 
Figure 34: Case study 3_Diferrence between IaaS, PaaS, and SaaS
![image](https://github.com/user-attachments/assets/348cb429-a9a4-4898-ad13-25ceee88efe2)

 
Figure 35: Knowledge Check Module 1

AWS Cost Analysis 
•	Objective
To analyze AWS pricing using the AWS Pricing Calculator and Cost Explorer. Understand Total Cost of Ownership - Delaware North and support plan from the case on model 2.
•	Tools and Services Used	
AWS Management Console, Cost Explorer, and Pricing Calculator 
![image](https://github.com/user-attachments/assets/14e8cc89-5ba7-4324-b3df-2afe3167ac68)


 
Figure 36: Case Study 4_Total Cost Of Ownership - Delaware North
![image](https://github.com/user-attachments/assets/194bfe65-882e-4930-9ae8-c7bb7092b4fc)


 
Figure 37: AWS Pricing Calculator
![image](https://github.com/user-attachments/assets/e6dc4f8c-8f6a-41cf-993f-47cb853b4ef8)

 
Figure 38: Case Study 6_Support Plan
![image](https://github.com/user-attachments/assets/12af09bd-0847-4b91-9357-2c9867acf4e7)


 
Figure 39: Knowledge Check Module 2
AWS Global infrastructure 
•	Objective
To explore the difference between Regional Edge Cache, Edge Location, and Region as per their location, access, and privacy.
•	Tools and Services Used
AWS Management Console and draw.io
![image](https://github.com/user-attachments/assets/0c988009-37ba-4ad8-9f4b-6777d7c93e6f)


 
Figure 40: Difference between Regional Edge Cache, Edge Location, and Region
![image](https://github.com/user-attachments/assets/7f4f483d-245e-4c74-b246-a3a7d756df98)

 
Figure 41: Knowledge Check Module 3


AWS IAM 
•	Objective
To understand UCW and AWS responsibility based on EC2, Platform, Software, and Dataset. And to configure secure access control using IAM users and roles.
•	Tools and Services Used
AWS Management Console, IAM, and draw.io
 ![image](https://github.com/user-attachments/assets/0375959f-4f3b-4b5f-aeb6-78848e36989c)


Figure 42: Case Study 8_ Responsible of UCW and AWS
![image](https://github.com/user-attachments/assets/0e0f98ef-78a9-4f01-9694-12fff4ae405f)

 
Figure 43: Lab 1-IAM Practice
![image](https://github.com/user-attachments/assets/0c194660-cf01-45ba-99d1-bbb6992c1df5)

 
Figure 44: Knowledge Check Module 4

AWS VPC
•	Objective
To create and manage a secure network using subnets, route tables, and gateways.
•	Tools and Services Used
AWS Management Console and VPC
![image](https://github.com/user-attachments/assets/d7a057dd-eb7c-4972-b6d4-1f5b91df588b)


 
Figure 45: Lab 2-Build your VPC
![image](https://github.com/user-attachments/assets/7c2b0692-6afd-4be8-9e11-b4ac6e4357c0)


 
Figure 46: Knowledge Check Module 
AWS Lambda 
•	Objective
To build a server less function triggered by S3 events to automate backend processing.
•	Tools and Services Used
AWS Management Console, S3, and Lambda
![image](https://github.com/user-attachments/assets/a99799a4-2c4c-4302-983c-ce11f6437bce)

 
Figure 47: Lab- Create an AWS Lambda function
![image](https://github.com/user-attachments/assets/ab14f2f6-30d4-48f5-9a0c-887cc6443071)

 
Figure 48: Knowledge Check Module 6

AWS EBS
•	Objective
To provision persistent block storage for EC2 and manage snapshots.
•	Tools and Services Used
AWS Management Console, EC2, and EBS
![image](https://github.com/user-attachments/assets/88c2f95f-f53c-4acc-9a75-e81a713310bf)


 
Figure 49: Lab 4_Working with Amazon EBS
![image](https://github.com/user-attachments/assets/f8cb8706-caa5-41ca-b0d8-a64f85ab1032)

 
Figure 50: Knowledge Check Module 7
Tools and Technologies

Microsoft Excel – For planning and organizing the data lake

Draw.io – To create diagrams

Fishbone Diagram – To find root causes of the forecasting issues

Amazon S3 – for organizing and storing cleaned datasets

AWS Glue – Data catalog and schema registry

AWS Glue DataBrew – Visual ETL tool for transformation

Amazon Athena – SQL queries on transformed data

Amazon CloudWatch – Billing alerts and monitoring

AWS Billing Dashboard – for monitoring and managing costs
