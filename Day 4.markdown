# Cloud-DevOps Learning - Day 4 
Date:13.7.2025

## Overview
This README documents the key learnings from Day 4 of the Cloud-DevOps learning session on July 13, 2025, focusing on provisioning AWS resources, demonstrating EC2, and understanding AWS pricing.

## How to Provision AWS Resources
AWS resources can be provisioned using the AWS Management Console, AWS CLI, or Infrastructure as Code (IaC) tools like Terraform or AWS CloudFormation. Below are the general steps for provisioning resources:

1. **Log in to AWS Management Console**:
   - Access the AWS Management Console using your credentials.
   - Ensure you have the necessary IAM permissions to create resources.

2. **Select a Service**:
   - Navigate to the desired service (e.g., EC2, S3, RDS) from the AWS Console dashboard.

3. **Configure the Resource**:
   - Specify configurations such as region, instance type, storage, and security settings.
   - Example: For EC2, choose an Amazon Machine Image (AMI), instance type, and configure networking (VPC, subnets).

4. **Review and Launch**:
   - Review configurations and launch the resource.
   - Use tags to organize resources for cost tracking and management.

5. **Verify Resource Status**:
   - Check the resource status in the AWS Console to ensure it is running or active.

*Best Practice*: Use IaC tools like CloudFormation for repeatable and automated provisioning to minimize errors.

## AWS EC2 Demonstration
The session included a hands-on demonstration of launching an EC2 instance. Key steps performed:

1. **Access EC2 Dashboard**:
   - From the AWS Console, navigate to the EC2 service.

2. **Launch Instance**:
   - Select an AMI (e.g., Amazon Linux 2).
   - Choose an instance type (e.g., t2.micro for free-tier eligibility).
   - Configure instance details: VPC, subnet, and IAM role.
   - Add storage (default 8GB EBS volume).
   - Configure security group: Allow SSH (port 22) for remote access.

3. **Key Pair Creation**:
   - Create or select an existing key pair for SSH access.
   - Download and secure the `.pem` file.

4. **Connect to Instance**:
   - Use SSH to connect to the instance (e.g., `ssh -i key.pem ec2-user@<public-ip>`).
   - Verify connectivity and perform basic commands (e.g., `sudo yum update`).

5. **Terminate Instance**:
   - Stop or terminate the instance from the EC2 dashboard to avoid unnecessary costs.

*Note*: Always terminate unused instances to optimize costs.

## AWS Pricing
AWS pricing is based on a pay-as-you-go model. Key concepts covered:

1. **Pricing Models**:
   - **On-Demand**: Pay per hour or second, no upfront commitment.
   - **Reserved Instances**: Commit to 1 or 3 years for discounted rates.
   - **Spot Instances**: Bid for unused capacity at lower costs, ideal for fault-tolerant workloads.
   - **Savings Plans**: Flexible pricing for compute usage across services.

2. **EC2 Pricing Example**:
   - t2.micro (free-tier eligible): Free for 750 hours/month for the first 12 months.
   - On-Demand t3.medium (us-east-1): ~$0.0416/hour (as of July 2025, verify current rates).
   - Additional costs: EBS volumes, data transfer, and Elastic IPs.

3. **Cost Management Tools**:
   - **AWS Cost Explorer**: Analyze and visualize spending.
   - **AWS Budgets**: Set custom cost and usage budgets.
   - **Trusted Advisor**: Provides cost optimization recommendations.

*Tip*: Use the AWS Pricing Calculator (https://calculator.aws) to estimate costs before provisioning resources.

## Key Takeaways
- Provisioning AWS resources requires careful configuration and IAM permissions.
- EC2 is a versatile service for running virtual servers, with easy setup and management.
- Understanding AWS pricing models helps optimize costs and avoid unexpected charges.

For more details, refer to the AWS documentation: https://docs.aws.amazon.com