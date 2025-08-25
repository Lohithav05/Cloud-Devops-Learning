# Cloud devops learning journey -Day 47
Date:25.08.25

## Project Overview
This project performs data analytics using Amazon Web Services (AWS) to derive insights from transactional sales data. The goal is to analyze sales trends and forecast demand using AWS analytics services. This README provides details on the dataset, AWS services, data processing workflows, and instructions for accessing and analyzing the data.

## Dataset Description
- Name: Transactional Sales Data
- Source: Internal company CRM system
- Size: 2 GB uncompressed, ~10 million rows
- Format: CSV
- Collection Period: 2025-01-01 to 2025-08-25
- Description: Contains customer transaction records including purchase date, amount, and product ID for sales trend analysis.
- Number of Variables: 6 columns
- Variable List:
  - purchase_date: Date of transaction (YYYY-MM-DD)
  - customer_id: Unique customer identifier (string)
  - product_id: Unique product identifier (string)
  - amount: Transaction value in USD (float)
  - region: Geographic region of sale (string)
  - status: Transaction status (e.g., COMPLETED, REFUNDED)
- Quality Notes: Missing values in `amount` for ~5% of records; outliers flagged with 'OUT' in `status`.

## AWS Services Used
- Amazon S3: Storage for raw and processed data in s3://my-analytics-bucket/.
- AWS Glue: Serverless ETL for data ingestion, transformation, and cataloging.
- Amazon Athena: Interactive SQL queries on S3 data.
- Amazon Redshift: Data warehouse for complex analytics.
- Amazon QuickSight: Dashboards for sales performance visualization.
- Amazon Kinesis Data Streams: Real-time streaming for near-real-time metrics.
- AWS Lambda: Event-driven processing for ETL triggers.
- Amazon SNS: Notifications for pipeline status or data quality alerts.

## File Structure
/my-analytics-bucket/
├── raw_data/                     # Raw CSV files
├── processed_data/               # Transformed Parquet files
├── glue_scripts/                 # AWS Glue ETL scripts (PySpark)
├── athena_queries/               # SQL queries for Athena
├── quicksight_dashboards/        # QuickSight dashboard configurations
└── README.txt                    # This file

## Data Processing Workflow
1. Ingestion: Data ingested into S3 via AWS Glue crawlers or Kinesis Data Streams.
2. Transformation: AWS Glue ETL jobs convert raw CSV to Parquet, with schema discovery and PII redaction.
3. Storage: Processed data stored in S3 with partitioning (e.g., by date/region) and compression.
4. Analysis: Athena for ad-hoc SQL queries; Redshift for aggregations.
5. Visualization: QuickSight dashboards refreshed every 5 minutes.
6. Alerts: Lambda and SNS send notifications for data quality issues or pipeline failures.

## Setup and Usage Instructions
1. Prerequisites:
   - AWS account with access to S3, Glue, Athena, Redshift, QuickSight, Kinesis, Lambda, SNS.
   - IAM roles configured for cross-service access.
   - Data files uploaded to s3://my-analytics-bucket/raw_data/.
2. Setup:
   - Deploy AWS CloudFormation stack from [template file, if applicable].
   - Configure Glue crawlers to catalog raw data in S3.
   - Set up Redshift cluster and load processed data.
   - Create QuickSight datasets and dashboards.
3. Usage:
   - Run Glue ETL jobs: `aws glue start-job --job-name my-etl-job`
   - Query data in Athena: `SELECT * FROM sales_data WHERE purchase_date >= '2025-08-01'`
   - Access QuickSight dashboards at [QuickSight URL or describe access method].
   - Monitor Kinesis streams and Lambda logs via CloudWatch.

## Access and Permissions
- Data Access: Restricted to [e.g., data analytics team] via IAM roles.
- S3 Bucket Policy: Read/write access for authorized roles only.
- Contact: [e.g., data-team@company.com] for access requests.

