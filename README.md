# Data-analytic
**DATA ANALYST PORTFOLIO - Arivudainambhi**

**Cloud Data Migration & Analytics** 

**Project Title:** AWS Data Analytics Platform Migration (City of Vancouver) 

**Project Summary:** The goal of this cloud project is to design and implement a Scalable Data Analytics Platform (DAP) for municipal data processing and insights. The project focuses on integrating structured and unstructured city data sources, including citizen reports, infrastructure records, and public safety information. This platform will utilize AWS cloud services to ensure scalability, security, and efficient data processing. The end-to-end pipeline will cover data ingestion, profiling, transformation, governance, and monitoring to support data-driven decision-making by city administrators. 
The solution leverages AWS services such as Amazon S3, AWS Glue, Amazon Athena, Amazon Redshift, AWS Lambda, and Amazon QuickSight for advanced analytics and visualization. 
**Project Title
Smart City Data Analytics: AWS-Based Infrastructure for Urban Insights**

**Objective**
The objective of this project is to develop a secure, scalable, and efficient cloud-based data analytics platform capable of:

Ingesting and processing structured and unstructured city data from multiple sources.

Profiling and cleaning the data to ensure quality and consistency.

Transforming raw data into optimized formats such as Parquet for efficient querying and storage.

Analyzing traffic patterns, service requests, and maintenance data for operational insights.

Enabling real-time dashboards for decision-makers using AWS analytics and visualization tools.

This project aims to enhance urban planning and public service efficiency by providing actionable insights from large-scale municipal datasets.

**Dataset:**
The platform will integrate multiple datasets related to city operations and services, categorized as follows:

**Citizen Reports (Structured Logs of Service Requests):**

Complaints and service requests related to infrastructure, sanitation, and utilities.

Fields include request type, timestamp, status, and location.

**Infrastructure Data (Maintenance & Inspection Records):**

Logs of maintenance activities for city assets such as roads, water supply, and power grids.

Fields include asset ID, maintenance type, last serviced date, and technician details.

**Traffic & Public Safety (Sensor & Surveillance Data):**

IoT-based real-time data from traffic sensors and safety cameras.

Includes traffic flow metrics, accident reports, and emergency response times.

Each dataset will be processed and transformed into an optimized format to enable efficient querying and predictive modeling for city administration.

  **Designing the data flow:** 
  <img width="884" alt="A1" src="https://github.com/user-attachments/assets/baa3dadd-c32d-40b1-a3e6-d48ac0ac8a98" />

**Setting up the S3 Bucket**
<img width="782" alt="A2" src="https://github.com/user-attachments/assets/2e24b9d9-78b0-44f8-881c-6fec85cd1459" />

To serve as a central repository for all raw data files, I set up an Amazon S3 bucket. I transferred data from my local system to Amazon S3 using PowerShell scripts. This enables data to be kept in the cloud for further processing and analysis. Data Verification for Ingestion: I checked the data within the AWS Management Console following the upload so that the files actually got stored correctly in the proper S3 bucket locations. 
**Data profiling**
<img width="797" alt="A3" src="https://github.com/user-attachments/assets/ffcb42e4-542d-404a-8625-2a464437f006" />
   I profiled and cleaned the water quality dataset using AWS Glue DataBrew to make it properly organized and ready for further analysis. The dataset, divided into sections such as cooling towers, decorative water features, and building water treatment facilities, was kept in an S3 bucket. An overview of data ingestion and processing pipeline is given by the Draw.io diagram that also describes storage, analysis, and transformation of various datasets.
   <img width="780" alt="A4" src="https://github.com/user-attachments/assets/b29f859e-98b4-430b-a62c-6ce884aed195" />

   After the datasets were set up, I used DataBrew to build profile jobs that examined the data quality and structure.  Profiling created insights into column data types, missing values, duplicate records, and variable correlation.  Missing values in the Cooling Tower dataset's Legionella Level CFU, pH Level, and Chlorine Levels, for instance, were found. Inconsistencies in data types and formatting were also discovered while profiling the Building Water Treatment and Decorative Water Feature datasets.
   <img width="792" alt="A5" src="https://github.com/user-attachments/assets/f1bf50f4-cde1-4f08-8a2e-bedd466c7f0b" />
   <img width="793" alt="A6" src="https://github.com/user-attachments/assets/d8f71a55-a9e4-410a-b8e7-ea1acddfbb70" />

**Data Cleaning**
I then conducted data cleaning to have the dataset properly organized, standardized, and ready for analysis once I had finished the data profiling process and discovered several data quality problems. I did this by creating a specific data cleaning action that fixed missing values, inconsistent data, improper delimiters, and storage format optimization. 
The "vwq-bwt-lst-cln-arivdai0402" data cleaning task was carried out using AWS Glue DataBrew. The dataset was refined using transformations in this task before being stored in an efficient manner. 

**Formatting Output and Optimizing Storage**
<img width="818" alt="A7" src="https://github.com/user-attachments/assets/0e3b30e2-6395-43b3-aa3e-ef4fb647a64b" />

I saved the dataset in two optimal forms following the cleaning procedure:
<img width="830" alt="A8" src="https://github.com/user-attachments/assets/f120ec4d-7e1e-4374-bb3f-65d1f5abaa2c" />

**Optimization of Storage and Cost**
Once the data were cleaned, the converted datasets were placed in the "user" and "system" directories of the "vwq-bwt-lst-arivudai0402" S3 bucket. 
Given that the dataset is refreshed frequently, I reduced storage costs by taking advantage of AWS S3 Lifecycle Rules. I maintained cost-effectiveness and quick access as needed by storing obsolete data in Amazon S3 Glacier Instant Retrieval. This helped me save a lot of money on long-term storage while not compromising data accessibility. 
<img width="803" alt="A9" src="https://github.com/user-attachments/assets/d346cc2f-0e4c-46e0-a835-191ea275ed94" />

**Using the AWS Glue Crawler**
I initiated the data transformation and extraction process by running the AWS Glue Crawler after setting up the configurations. The tables created were examined in the AWS Glue Data Catalog after they were complete. 
<img width="815" alt="A10" src="https://github.com/user-attachments/assets/2cde05be-2b1c-4dd9-8788-8d5aaa6ca788" />

**Results of creating a data catalog:**
The data was indexed successfully into structured tables that could be queried using Redshift, Amazon Athena, or other services. The data will remain well-structured and readily available for additional processing thanks to this orderly process. 
<img width="800" alt="A11" src="https://github.com/user-attachments/assets/cf1cf2e2-7072-4c99-bb7f-6c38e612eff7" />

**Data Summarization**
AWS Glue Visual ETL proved useful to enable such a change, enabling data transformation without too much coding. To make the pipeline of data processing set up for summarizing efficiently, a new Visual ETL job called "cooling-tower-list-Summarization" was established. 
<img width="564" alt="A12" src="https://github.com/user-attachments/assets/f76bd54d-c1d6-4150-80e8-a0c923f53131" />

AWS Glue was provided with the required IAM permissions to allow access to the appropriate S3 buckets and tables prior to triggering the data transformation process. This made it possible for the ETL pipeline to load, extract, and transform data into the corresponding locations with ease. AWS Glue Data Catalog was chosen as the source of data for the ETL process, allowing structured data sets to be fetched with ease without the need for manual data extraction. 
<img width="610" alt="A13" src="https://github.com/user-attachments/assets/3abdef16-a9c5-48c6-b922-ef5ab9d7530a" />

The information was well-structured and ready for additional analysis and reporting by adopting an ETL pipeline, providing easy access to summarized information for well-informed decision-making. 
**Monthly Cost** 
<img width="601" alt="A14" src="https://github.com/user-attachments/assets/d1cd1ef0-3269-4c88-9cca-95dcd9705aa4" />

The expense on the site is shown on the AWS Billing and Cost Management Dashboard. The overall estimated cost this month is $7.69, with the expense so far being $1.75. This is a 5,217%  
**Recommendations:** 
Improve operational efficiency through predictive insights. 
Tools & Technologies 
AWS (S3, Redshift, Glue, Lambda, Athena, CloudTrail, GuardDuty) 
**Deliverables** 
AWS solution architecture and migration plan. 


**References**

AWS Documentation. (n.d.). Amazon S3: Object Storage Service. Retrieved from https://aws.amazon.com/s3/ 

AWS Glue. (n.d.). AWS Glue DataBrew Overview. Retrieved from https://aws.amazon.com/glue/databrew/ 

City of Vancouver Open Data Portal. (n.d.). Water Quality Data. Retrieved from https://opendata.vancouver.ca  

AWS Cost Management. (n.d.). Billing Dashboard Overview. Retrieved from https://aws.amazon.com/aws-cost-management/ 

