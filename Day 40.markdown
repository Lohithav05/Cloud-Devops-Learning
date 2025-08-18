# Cloud devops learning journey-Day 40
Date:August 18, 2025

## Overview
This project demonstrates the basic operations of **Amazon Simple Storage Service (Amazon S3)** using the AWS SDK for Python (Boto3). It covers creating an S3 bucket, uploading and downloading files, copying objects within a bucket, listing bucket contents, and cleaning up resources. This is intended for developers looking to understand S3 fundamentals through a practical example.

## Prerequisites
- **AWS Account**: Ensure you have an active AWS account with appropriate permissions to access S3.
- **AWS CLI Configured**: Set up AWS credentials (`aws configure`) with access key, secret key, and default region.
- **Python 3.7+**: Install Python on your system.
- **Boto3 Library**: Install using `pip install boto3`.
- **Basic Python Knowledge**: Familiarity with Python scripting is helpful.

## Setup Instructions
1. **Clone the Repository** (if applicable):
   ```bash
   git clone <repository-url>
   cd amazon-s3-demo
   ```
2. **Install Dependencies**:
   ```bash
   pip install boto3
   ```
3. **Configure AWS Credentials**:
   Run `aws configure` and provide your AWS Access Key ID, Secret Access Key, and default region (e.g., `us-east-1`).

## Demonstration Steps
The sample script (`s3_demo.py`) performs the following operations:
1. **Create a Bucket**: Creates an S3 bucket with a unique name.
2. **Upload a File**: Uploads a sample text file to the bucket.
3. **Download a File**: Downloads the uploaded file to the local system.
4. **Copy an Object**: Copies the file to a simulated folder within the bucket.
5. **List Bucket Contents**: Lists all objects in the bucket.
6. **Clean Up**: Deletes the objects and the bucket.

### Sample Code
Below is the Python script used for this demonstration:

```python
import boto3
import uuid
import os

# Initialize the S3 client
s3_client = boto3.client('s3')

def create_bucket(bucket_name, region='us-east-1'):
    try:
        if region == 'us-east-1':
            s3_client.create_bucket(Bucket=bucket_name)
        else:
            s3_client.create_bucket(
                Bucket=bucket_name,
                CreateBucketConfiguration={'LocationConstraint': region}
            )
        print(f"Bucket {bucket_name} created successfully.")
        return True
    except Exception as e:
        print(f"Error creating bucket: {e}")
        return False

def upload_file(file_path, bucket_name, object_key):
    try:
        s3_client.upload_file(file_path, bucket_name, object_key)
        print(f"File {file_path} uploaded to {bucket_name}/{object_key}.")
        return True
    except Exception as e:
        print(f"Error uploading file: {e}")
        return False

def download_file(bucket_name, object_key, download_path):
    try:
        s3_client.download_file(bucket_name, object_key, download_path)
        print(f"File {object_key} downloaded to {download_path}.")
        return True
    except Exception as e:
        print(f"Error downloading file: {e}")
        return False

def copy_object(bucket_name, source_key, destination_key):
    try:
        s3_client.copy_object(
            Bucket=bucket_name,
            CopySource={'Bucket': bucket_name, 'Key': source_key},
            Key=destination_key
        )
        print(f"Object {source_key} copied to {destination_key}.")
        return True
    except Exception as e:
        print(f"Error copying object: {e}")
        return False

def list_objects(bucket_name):
    try:
        response = s3_client.list_objects_v2(Bucket=bucket_name)
        if 'Contents' in response:
            print("Objects in bucket:")
            for obj in response['Contents']:
                print(f" - {obj['Key']}")
        else:
            print("Bucket is empty.")
        return True
    except Exception as e:
        print(f"Error listing objects: {e}")
        return False

def delete_bucket_contents(bucket_name):
    try:
        response = s3_client.list_objects_v2(Bucket=bucket_name)
        if 'Contents' in response:
            objects = [{'Key': obj['Key']} for obj in response['Contents']]
            s3_client.delete_objects(Bucket=bucket_name, Delete={'Objects': objects})
            print(f"All objects in {bucket_name} deleted.")
        return True
    except Exception as e:
        print(f"Error deleting objects: {e}")
        return False

def delete_bucket(bucket_name):
    try:
        s3_client.delete_bucket(Bucket=bucket_name)
        print(f"Bucket {bucket_name} deleted.")
        return True
    except Exception as e:
        print(f"Error deleting bucket: {e}")
        return False

def main():
    # Generate a unique bucket name
    bucket_name = f"demo-s3-bucket-{uuid.uuid4().hex}"
    file_path = "sample.txt"
    object_key = "sample.txt"
    download_path = "downloaded_sample.txt"
    folder_key = "files/sample.txt"

    # Create a sample file
    with open(file_path, 'w') as f:
        f.write("This is a sample file for S3 demo.")

    # Execute S3 operations
    if create_bucket(bucket_name):
        upload_file(file_path, bucket_name, object_key)
        download_file(bucket_name, object_key, download_path)
        copy_object(bucket_name, object_key, folder_key)
        list_objects(bucket_name)
        delete_bucket_contents(bucket_name)
        delete_bucket(bucket_name)

    # Clean up local files
    if os.path.exists(file_path):
        os.remove(file_path)
    if os.path.exists(download_path):
        os.remove(download_path)

if __name__ == "__main__":
    main()
```

## Running the Demo
1. Save the above code as `s3_demo.py`.
2. Run the script:
   ```bash
   python s3_demo.py
   ```
3. Follow the console output to see the results of each operation.

## Expected Output
```
Bucket demo-s3-bucket-<unique-id> created successfully.
File sample.txt uploaded to demo-s3-bucket-<unique-id>/sample.txt.
File sample.txt downloaded to downloaded_sample.txt.
Object sample.txt copied to files/sample.txt.
Objects in bucket:
 - sample.txt
 - files/sample.txt
All objects in demo-s3-bucket-<unique-id> deleted.
Bucket demo-s3-bucket-<unique-id> deleted.
```
