# Cloud devops learning journey-Day 43
Date:21.08.2025

This README provides an overview of Amazon RDS and Amazon DynamoDB, two popular AWS database services, and includes a demonstration of how to set them up and interact with them using Python and the AWS SDK (Boto3).

## Overview

### Amazon RDS (Relational Database Service)
Amazon RDS is a fully managed relational database service that supports multiple database engines, including MySQL, PostgreSQL, MariaDB, Oracle, SQL Server, and Amazon Aurora. It automates tasks like hardware provisioning, database setup, patching, and backups, allowing developers to focus on application development. RDS is ideal for structured data requiring complex queries, joins, and transactional consistency.

- **Key Features**:
  - Supports relational database engines (e.g., MySQL, PostgreSQL).
  - Vertical scaling (increasing instance resources) and read replicas for horizontal scaling.
  - Automated backups, multi-AZ deployments for high availability, and integration with AWS services like CloudWatch and S3.
  - Suitable for applications like e-commerce platforms, content management systems, and enterprise applications requiring structured data.
  - Security features include encryption at rest, IAM integration, and VPC support.

- **Use Cases**:
  - Applications requiring complex SQL queries and relational data models.
  - Scenarios needing strong consistency and transactional support.
  - Traditional enterprise applications migrating to the cloud.

### Amazon DynamoDB
Amazon DynamoDB is a fully managed, serverless NoSQL database designed for high-performance, scalable applications. It supports key-value and document data models, offering low-latency reads and writes at any scale. DynamoDB is ideal for unstructured or semi-structured data and serverless architectures.

- **Key Features**:
  - Serverless, with automatic scaling and no need to manage servers.
  - Consistent single-digit millisecond performance.
  - Global tables for multi-region replication with 99.999% availability.
  - Integration with AWS services like Lambda, S3, and Kinesis for event-driven architectures.
  - Encryption at rest, IAM for access control, and point-in-time recovery (PITR).

- **Use Cases**:
  - High-traffic web and mobile applications (e.g., gaming, social media).
  - Real-time analytics, event-driven applications, and IoT data storage.
  - Workloads requiring flexible schemas and massive scalability.

## Demonstration: Using Amazon RDS and DynamoDB with AWS Services

This section demonstrates how to:
1. Set up an Amazon RDS MySQL instance and interact with it using Python.
2. Create a DynamoDB table and perform basic CRUD operations using Python.
3. Highlight integration with AWS services (e.g., Lambda for DynamoDB, CloudWatch for RDS monitoring).

### Prerequisites
- An AWS account with appropriate permissions (`DynamoDBFullAccess`, `AmazonRDSFullAccess`, and `AWSCloud9Administrator` recommended).
- Python 3.x installed with the Boto3 library (`pip install boto3`).
- AWS CLI configured with access key and secret key.
- A MySQL client (e.g., MySQL Workbench or `mysql` CLI) for RDS interaction.

### 1. Amazon RDS Setup and Demonstration
This demonstration sets up a MySQL database using Amazon RDS and performs basic operations using Python.

#### Step 1: Create an RDS MySQL Instance
1. Log in to the AWS Management Console.
2. Navigate to **Amazon RDS** > **Create database**.
3. Choose:
   - **Engine**: MySQL (e.g., version 8.0).
   - **Template**: Free Tier (for testing).
   - **DB instance identifier**: `my-mysql-db`.
   - **Master username**: `admin`.
   - **Master password**: Set a secure password.
   - **Instance class**: `db.t3.micro` (Free Tier eligible).
   - **Storage**: 20 GB (Free Tier default).
   - **VPC settings**: Default VPC, enable public access (for testing).
4. Click **Create database**. Note the endpoint and port after creation (e.g., `my-mysql-db.xxxxxxxxxxxx.us-east-1.rds.amazonaws.com:3306`).

#### Step 2: Connect to RDS and Perform Operations
Use the following Python script to connect to the RDS MySQL instance, create a table, insert data, and query it.

```python
import pymysql

# RDS connection details
host = 'my-mysql-db.xxxxxxxxxxxx.us-east-1.rds.amazonaws.com'
port = 3306
user = 'admin'
password = 'your_secure_password'
database = 'mydb'

# Connect to RDS
connection = pymysql.connect(
    host=host,
    port=port,
    user=user,
    password=password,
    database=database
)

try:
    with connection.cursor() as cursor:
        # Create a table
        cursor.execute("""
            CREATE TABLE IF NOT EXISTS users (
                id INT AUTO_INCREMENT PRIMARY KEY,
                name VARCHAR(255),
                email VARCHAR(255)
            )
        """)
        connection.commit()

        # Insert data
        cursor.execute("INSERT INTO users (name, email) VALUES (%s, %s)", ('John Doe', 'john@example.com'))
        connection.commit()

        # Query data
        cursor.execute("SELECT * FROM users")
        results = cursor.fetchall()
        for row in results:
            print(row)

finally:
    connection.close()
```

#### Step 3: Integration with AWS Services
- **Monitoring**: Use Amazon CloudWatch to monitor RDS metrics like CPU utilization, database connections, and I/O operations. Navigate to **CloudWatch** > **Metrics** > **RDS** to view.
- **Backup**: Enable automated backups in the RDS console (default for Free Tier) or create manual snapshots.
- **Scaling**: Add read replicas via the RDS console to offload read traffic or scale vertically by modifying the instance type.

### 2. Amazon DynamoDB Setup and Demonstration
This demonstration creates a DynamoDB table and performs CRUD operations using Python.

#### Step 1: Create a DynamoDB Table
1. Log in to the AWS Management Console.
2. Navigate to **Amazon DynamoDB** > **Tables** > **Create table**.
3. Configure:
   - **Table name**: `Users`.
   - **Partition key**: `Id` (String).
   - **Sort key**: `Email` (String, optional for range queries).
   - **Settings**: Use default (on-demand capacity for simplicity).
4. Click **Create table**.

#### Step 2: Perform CRUD Operations
Use the following Python script to interact with the DynamoDB table.

```python
import boto3

# Initialize DynamoDB client
dynamodb = boto3.resource('dynamodb', region_name='us-east-1')
table = dynamodb.Table('Users')

# Create (Put item)
table.put_item(
    Item={
        'Id': '1',
        'Email': 'jane@example.com',
        'Name': 'Jane Doe'
    }
)

# Read (Get item)
response = table.get_item(
    Key={
        'Id': '1',
        'Email': 'jane@example.com'
    }
)
print("Get Item:", response.get('Item'))

# Update
table.update_item(
    Key={
        'Id': '1',
        'Email': 'jane@example.com'
    },
    UpdateExpression='SET Name = :val',
    ExpressionAttributeValues={
        ':val': 'Jane Smith'
    }
)

# Delete
table.delete_item(
    Key={
        'Id': '1',
        'Email': 'jane@example.com'
    }
)

# Query
response = table.query(
    KeyConditionExpression='Id = :id',
    ExpressionAttributeValues={
        ':id': '1'
    }
)
print("Query Results:", response['Items'])
```

#### Step 3: Integration with AWS Services
- **AWS Lambda**: Create a Lambda function to trigger on DynamoDB Streams for real-time data processing. For example, log changes to CloudWatch when an item is added.
  - In the Lambda console, create a function with a DynamoDB trigger linked to the `Users` table stream.
  - Example Lambda code:
    ```python
    import json

    def lambda_handler(event, context):
        for record in event['Records']:
            print("DynamoDB Record:", json.dumps(record['dynamodb'], indent=2))
        return {
            'statusCode': 200,
            'body': json.dumps('Processed DynamoDB stream!')
        }
    ```
- **Amazon S3**: Export DynamoDB table data to S3 for analytics using the DynamoDB console (Tables > Exports and streams > Export to S3).
- **Monitoring**: Use CloudWatch to monitor DynamoDB metrics like read/write capacity units and latency.

### Choosing Between RDS and DynamoDB
- **Use RDS** when:
  - You need a relational database with complex queries, joins, and transactions.
  - Your data is structured and requires strong consistency.
  - Examples: E-commerce order processing, CRM systems.
- **Use DynamoDB** when:
  - You need a NoSQL database with high scalability and low-latency performance.
  - Your data is unstructured or semi-structured, and access patterns are known.
  - Examples: Real-time analytics, mobile app backends, gaming leaderboards.

### Cleanup
To avoid charges:
- **RDS**: Delete the DB instance (`my-mysql-db`) via the RDS console.
- **DynamoDB**: Delete the `Users` table via the DynamoDB console.
- **Other Resources**: Remove any Lambda functions, CloudWatch logs, or S3 buckets created during testing.

### Additional Resources
- [Amazon RDS Documentation](https://docs.aws.amazon.com/rds/)
- [Amazon DynamoDB Documentation](https://docs.aws.amazon.com/dynamodb/)
- [AWS SDK for Python (Boto3)](https://boto3.amazonaws.com/v1/documentation/api/latest/index.html)
- [AWS Free Tier](https://aws.amazon.com/free/) for cost-free experimentation.

**Note**: This demonstration uses AWS Free Tier-eligible resources where possible, but some actions may incur costs. Check [Amazon RDS Pricing](https://aws.amazon.com/rds/pricing/) and [Amazon DynamoDB Pricing](https://aws.amazon.com/dynamodb/pricing/) for details.