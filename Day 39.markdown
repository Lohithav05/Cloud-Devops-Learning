# Cloud devops learning journey-Day 39
Date:17.08.2025

## Overview
This project demonstrates **Amazon S3** for scalable object storage. It includes scripts to create buckets, upload objects with metadata, enable versioning, and configure event notifications.

## Prerequisites
- AWS Account with IAM permissions for S3 (`s3:CreateBucket`, `s3:PutObject`, etc.).
- AWS CLI installed and configured (`aws configure`).
- Python 3.8+ with Boto3 (`pip install boto3`).

## Setup
1. **Create Bucket**:
   ```bash
   aws s3api create-bucket --bucket my-unique-bucket-2025 --region us-east-1
   aws s3api put-bucket-versioning --bucket my-unique-bucket-2025 --versioning-configuration Status=Enabled
   aws s3api put-bucket-encryption --bucket my-unique-bucket-2025 --server-side-encryption-configuration '{"Rules": [{"ApplyServerSideEncryptionByDefault": {"SSEAlgorithm": "AES256"}}]}'
   ```

## Usage
### Upload Objects with Metadata
**AWS CLI**:
```bash
aws s3api put-object --bucket my-unique-bucket-2025 --key docs/sample.txt --body sample.txt --metadata "author=User,project=S3Demo"
```

**Python (Boto3)**:
```python
import boto3
s3_client = boto3.client('s3')
s3_client.put_object(
    Bucket='my-unique-bucket-2025',
    Key='docs/sample.txt',
    Body=open('sample.txt', 'rb'),
    Metadata={'author': 'User', 'project': 'S3Demo'}
)
```

### List Objects by Date
```bash
aws s3api list-objects-v2 --bucket my-unique-bucket-2025 --query 'Contents[?contains(LastModified, `2025-08-17`)].Key'
```

### Event Notifications
Configure S3 to trigger a Lambda function:
```bash
aws s3api put-bucket-notification-configuration --bucket my-unique-bucket-2025 --notification-configuration '{"LambdaFunctionConfigurations": [{"LambdaFunctionArn": "arn:aws:lambda:us-east-1:123456789012:function:my-function", "Events": ["s3:ObjectCreated:*"]}]}'
```

## Features
- **Metadata**: Add/query custom metadata.
- **Versioning**: Enabled for object history.
- **Encryption**: AES-256 by default.
- **Events**: Trigger Lambda on object creation.

## Best Practices
- Use unique bucket names (e.g., `my-unique-bucket-2025-xyz`).
- Block public access:
  ```bash
  aws s3api put-public-access-block --bucket my-unique-bucket-2025 --public-access-block-configuration "BlockPublicAcls=true,IgnorePublicAcls=true,BlockPublicPolicy=true,RestrictPublicBuckets=true"
  ```
- Use S3 Intelligent-Tiering for cost savings.

