# Project Overview

This project focuses on developing a scalable data engineering pipeline using AWS to manage and analyze COVID-19 data from various sources. Data is ingested via S3, processed using Python scripts for transformation, and loaded into Amazon Redshift for storage. Tools like AWS Glue for ETL and Amazon QuickSight for visualization are employed, with Python scripts run locally to connect and interact with AWS services. This project demonstrates practical application of cloud computing, data transformation, and visualization to support public health research and response. Also, creating a real-time dashboard using Amazon Quicksight. 

## Data Sources

The project involves using AWS's centralized repository of curated datasets related to COVID-19:
- COVID-19 Data Hub
- USA Hospital Beds by Rearc
- Definitive Healthcare
- Foursquare Foot Traffic Data

## Research Support

The data lake supports research such as pandemic-surveillance methods by Northwestern University, helping track and visualize COVID-19's spread to inform public health responses.

## Access and Tools Used

- **AWS CLI**
- **Amazon SageMaker**
- **AWS Glue**
- **Amazon S3**
- **Amazon Redshift**
- **Amazon Athena**
- **AWS Data Exchange**
- **AWS Quicksight**

## Analysis

Build a dashboard using Amazon Quicksight where Redshift is integrated with Quicksight to find insights about the COVID-19 analysis.

![image12](https://github.com/user-attachments/assets/f2bb106c-e0e2-4c14-851b-72add7db56e9)

## Steps to Implement the Project

### Step 1: Add CSV Files to Amazon S3

Upload your CSV files into an Amazon S3 bucket.


![image6](https://github.com/user-attachments/assets/2ecc8af3-ea82-4fa6-813a-4b51b8f1bd50)


### Step 2: Create Crawlers in AWS Glue

- Create crawlers for each dataset in AWS Glue. 
- AWS Glue will create a data catalog for each dataset.
- Use Athena to query the tables. Athena will find these tables with the help of the crawler created.
- Create a database for storing the crawled data.
  

![image10](https://github.com/user-attachments/assets/4429ec67-0f4f-4667-b992-2960ea5ac809)

While crawling, we need to create a database so that the crawled data can be stored into the same. 


![image9](https://github.com/user-attachments/assets/41074bc0-a6d8-4cdc-9b96-9cb1b56c310e)



### Step 3: Set Up Athena for SQL Queries

- Create an additional S3 bucket for Athena to store metadata and query results.
- Attach the S3 bucket to Athena.
- After data is crawled, it will appear in the Tables section in Amazon Athena, ready for SQL queries.

<img width="872" alt="image11" src="https://github.com/user-attachments/assets/02d62961-0b50-423c-b393-7f95e0e7c504">


<img width="976" alt="image3" src="https://github.com/user-attachments/assets/ef69483d-ff13-40e9-8001-5c4c9b56de25">


### Step 4: Build a Dimensional Model

**Data model**

<img width="748" alt="image1" src="https://github.com/user-attachments/assets/46d7d72c-7910-42be-af1c-e9778a7516e4">


**Dimensional model**


<img width="701" alt="image8" src="https://github.com/user-attachments/assets/6553e186-5892-4175-b3d0-1e654e00f089">



**Data Model:**
- Defines structure and organization of data in databases.
- Components: Entities, attributes, relationships, keys, constraints.
- Focus: Data storage and management.
- Usage: OLTP systems.

**Dimensional Model:**
- Optimized for data retrieval and analysis.
- Components: Fact tables (measures), dimension tables (descriptive attributes).
- Focus: Query efficiency and business user understanding.
- Usage: OLAP systems.

**OLTP vs. OLAP:**
- **OLTP:** Manages day-to-day transactions, high transaction volume, normalized data.
- **OLAP:** Supports complex queries and data analysis, read-heavy operations, denormalized data.

**Normalized vs. Denormalized Data:**
- **Normalized Data:** Reduce redundancy, improve data integrity, many related tables, used in OLTP systems.
- **Denormalized Data:** Improve query performance, fewer tables, more redundancy, used in OLAP systems.

### Step 5: ETL Transformations in Python

- Connect to your AWS account.
- Create functions to select and display each table from the database.
- Transform datasets into proper formats, such as adjusting date formats and setting headers.
- Build a star schema by joining tables to create fact and dimension tables.
- Store the final tables back into the Amazon S3 bucket.


![image4](https://github.com/user-attachments/assets/548b46d5-2e72-47e4-9f7c-d598a1176ebd)


### Step 6: Load Data into Redshift

- Verify data display correctness.
- Create a VPC Security group around a Redshift cluster before connecting it to Quicksight.

**Security Reasons:**
- **Isolation:** Ensures only allowed resources can access Redshift.
- **Control:** Manage inbound and outbound traffic through security groups and network ACLs.

**Network Accessibility:**
- **Private Network Access:** Avoid data exposure over the public internet.
- **Latency and Performance:** Reduced network latency improves query and dashboard performance.

**Data Integration:**
- **Direct Connectivity:** Real-time or near-real-time data analysis without intermediate data transfer.
- **Automated Configuration:** AWS automates network configuration for seamless integration.

![image13](https://github.com/user-attachments/assets/744a12c4-5fde-498f-be87-92dbb61fb4ca)

![image7](https://github.com/user-attachments/assets/24c01b2e-a2f3-45de-b157-cf82064103fa)

![image5](https://github.com/user-attachments/assets/ad0995ce-808d-49de-94db-2732130cde80)



### Step 7: Visualizing on Amazon Quicksight

- Build dashboards and find insights from the data.

**Insights:**
- VA Hospitals contribute significantly to the dataset with various hospital types.
- Positive records are highest in Australia, South Korea, and Hong Kong.
- The number of Fips records increased from 354 in 2020 to 2,751 in 2021.
- California, Missouri, and New York lead in Fips records among states.
- Illinois, Indiana, and Massachusetts have over 200 records each.
  

![image2](https://github.com/user-attachments/assets/343cb005-abdc-4ab7-a9a0-f140d3f3663a)


---

By utilizing these AWS tools, the project aims to demonstrate the powerful capabilities of cloud computing in managing, analyzing, and visualizing large datasets to derive meaningful insights.


