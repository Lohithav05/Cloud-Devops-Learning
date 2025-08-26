# Cloud devops learing journey-Day 48
Date:26.08.25

## Overview
AWS Data Pipeline is a managed ETL (Extract, Transform, Load) service that automates the movement and transformation of data across AWS services (e.g., Amazon S3, RDS, DynamoDB, Redshift) and on-premises data sources. It enables users to define data-driven workflows, schedule tasks, and manage dependencies, ensuring reliable and scalable data processing. Note: AWS Data Pipeline is no longer available to new customers, but existing customers can continue using it. For new projects, consider alternatives like AWS Glue.[](https://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/what-is-datapipeline.html)

This README provides an introduction to AWS Data Pipeline, its key components, and an example pipeline definition.

## Key Components
AWS Data Pipeline consists of the following core components:
- **Pipeline Definition**: Specifies the business logic, including data sources, transformations, and schedules.
- **Data Nodes**: Define the location and type of data (e.g., S3DataNode, SqlDataNode, DynamoDBDataNode, RedshiftDataNode).
- **Activities**: Define the processing tasks (e.g., CopyActivity, ShellCommandActivity, HiveActivity).
- **Schedules**: Set the timing and frequency of pipeline activities.
- **Task Runners**: Execute tasks on compute resources (e.g., EC2 instances or on-premises hosts).
- **Preconditions**: Ensure conditions are met before tasks run (e.g., data availability).
- **Resources**: Compute resources like EC2 instances or EMR clusters used for processing.

## Benefits
- **Automation**: Streamlines data movement and processing with minimal manual intervention.
- **Scalability**: Handles large-scale data workflows efficiently.
- **Fault Tolerance**: Automatically retries failed tasks and sends failure notifications.
- **Flexibility**: Supports both AWS and on-premises data sources.[](https://hevodata.com/learn/what-is-aws-data-pipeline/)

## Getting Started
1. **Create a Pipeline**:
   - Use the AWS Management Console, AWS CLI, or SDKs to define a pipeline.
   - Write a pipeline definition in JSON format, specifying data nodes, activities, and schedules.
2. **Upload and Activate**:
   - Upload the pipeline definition using the AWS CLI command `aws datapipeline put-pipeline-definition`.
   - Activate the pipeline with `aws datapipeline activate-pipeline`.
3. **Monitor and Verify**:
   - Monitor pipeline execution via the AWS Management Console or CLI.
   - Verify output data in the destination (e.g., S3 bucket).[](https://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-copydata-redshift-upload-cli.html)[](https://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-importexport-ddb-pipelinejson-verifydata2.html)

## Example Pipeline Definition
Below is an example JSON pipeline definition that copies data from an Amazon S3 bucket to another S3 bucket using a ShellCommandActivity.

```json
{
  "objects": [
    {
      "id": "Default",
      "name": "Default",
      "scheduleType": "CRON",
      "failureAndRerunMode": "CASCADE",
      "role": "DataPipelineDefaultRole",
      "resourceRole": "DataPipelineDefaultResourceRole",
      "schedule": { "ref": "Schedule_15mins" },
      "pipelineLogUri": "s3://mybucket/logs/"
    },
    {
      "id": "S3InputLocation",
      "name": "S3InputLocation",
      "type": "S3DataNode",
      "directoryPath": "s3://input-bucket/data"
    },
    {
      "id": "S3OutputLocation",
      "name": "S3OutputLocation",
      "type": "S3DataNode",
      "directoryPath": "s3://output-bucket/#{format(@scheduledStartTime, 'YYYY-MM-dd-HH-mm-ss')}"
    },
    {
      "id": "ShellCommandActivityObj",
      "name": "ShellCommandActivityObj",
      "type": "ShellCommandActivity",
      "command": "cp ${INPUT1_STAGING_DIR}/* ${OUTPUT1_STAGING_DIR}/",
      "input": { "ref": "S3InputLocation" },
      "output": { "ref": "S3OutputLocation" },
      "runsOn": { "ref": "EC2ResourceObj" },
      "stage": "true"
    },
    {
      "id": "EC2ResourceObj",
      "name": "EC2ResourceObj",
      "type": "Ec2Resource",
      "instanceType": "t1.micro",
      "terminateAfter": "20 Minutes"
    },
    {
      "id": "Schedule_15mins",
      "name": "Every 15 minutes",
      "type": "Schedule",
      "period": "15 Minutes",
      "startAt": "FIRST_ACTIVATION_DATE_TIME",
      "occurrences": "4"
    }
  ]
}
```

## Usage Instructions
1. Save the pipeline definition as `pipeline.json`.
2. Create a pipeline using:
   ```bash
   aws datapipeline create-pipeline --name my-pipeline --unique-id my-pipeline
   ```
3. Upload the pipeline definition:
   ```bash
   aws datapipeline put-pipeline-definition --pipeline-id <pipeline-id> --pipeline-definition file://pipeline.json
   ```
4. Activate the pipeline:
   ```bash
   aws datapipeline activate-pipeline --pipeline-id <pipeline-id>
   ```
5. Monitor execution using the AWS CLI or Management Console. Check output in the specified S3 bucket.[](https://github.com/amazon-archives/data-pipeline-samples)



