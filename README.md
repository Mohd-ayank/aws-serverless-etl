# aws-serverless-etl

**1. Project Overview**

This project implements a serverless, event-driven ETL pipeline on AWS to automate the ingestion and cleaning of raw CSV data. Whenever a file is uploaded to an Amazon S3 bucket, the pipeline automatically processes it using an AWS Lambda function written in Python and stores the cleaned output in a separate S3 bucket. The goal is to eliminate manual data cleaning and demonstrate a real-world cloud data processing workflow.

**2. Architecture**

Amazon S3 (Raw Data) -> AWS Lambda (Trigger + Processing) -> Amazon S3 (Clean Data)

This architecture follows a simple and scalable design where storage events drive computation, making the system efficient and cost-effective.

**3. How It Works**

**Extract:**
A CSV file is uploaded to the raw data S3 bucket.

**Transform:**
The upload event triggers a Lambda function that:

-> Loads the CSV file into a Pandas DataFrame.

-> Removes rows with missing or invalid values.

-> Standardizes column names for consistency.

**Load:**
The cleaned dataset is written back to a separate S3 bucket as a new CSV file, making it ready for downstream analytics or reporting tools such as Amazon Athena or Tableau.

**4. Key Features**

**Event-Driven Automation:**
The pipeline is triggered automatically using S3 event notifications whenever a new CSV file is uploaded.

**Serverless Processing:**
AWS Lambda is used for data transformation, removing the need to manage servers while allowing the pipeline to scale automatically.

**Data Cleaning & Standardization:**
The Lambda function performs basic data quality checks such as handling missing values, normalizing column names, and filtering invalid records.

**Secure Access Control:**
IAM roles are configured with least-privilege permissions to securely control access between Lambda and S3.

**5. Technologies Used**

**Cloud Services:** AWS S3, AWS Lambda, IAM

**Programming Language:** Python 3.9

**Libraries:** Pandas, Boto3, NumPy
