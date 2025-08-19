# Cloud devops learning journey-Day 41
Date:August 19, 2025

## Overview
Amazon Elastic File System (EFS) is a fully managed, serverless, and scalable file storage service provided by AWS. It is designed to provide shared file storage for multiple AWS compute instances, such as Amazon EC2, ECS, EKS, AWS Fargate, and Lambda, as well as on-premises servers via AWS Direct Connect or VPN. EFS supports the Network File System (NFS) protocol (NFSv4.0 and NFSv4.1) and is optimized for low-latency, high-throughput workloads, making it suitable for use cases like big data analytics, content management, web serving, and home directories.[](https://docs.aws.amazon.com/efs/latest/ug/whatisefs.html)[](https://aws.amazon.com/efs/features/)

## Key Features
- **Elastic Storage**: Automatically scales from gigabytes to petabytes as files are added or removed, with no need for manual provisioning. You pay only for the storage used.[](https://docs.aws.amazon.com/efs/latest/ug/whatisefs.html)[](https://aws.amazon.com/efs/faq/)
- **High Availability and Durability**: EFS Regional file systems store data redundantly across multiple Availability Zones (AZs) for 99.999999999% (11 nines) durability and up to 99.99% (4 nines) availability. EFS One Zone file systems store data in a single AZ at a lower cost but with reduced durability.[](https://aws.amazon.com/efs/features/)[](https://aws.amazon.com/efs/pricing/)
- **Performance Modes**:
  - **General Purpose**: Ideal for latency-sensitive applications like web servers and content management systems, supporting up to 35,000 read operations per second and 7,000 write operations per second.[](https://aws.amazon.com/about-aws/whats-new/2020/04/amazon-elastic-file-system-announces-increase-in-read-operations-for-general-purpose-file-systems/)
  - **Max I/O**: Optimized for high-throughput workloads with slightly higher latency, supporting over 500,000 operations per second.[](https://aws.amazon.com/about-aws/whats-new/2020/04/amazon-elastic-file-system-announces-increase-in-read-operations-for-general-purpose-file-systems/)
- **Throughput Modes**:
  - **Elastic Throughput**: Default mode, automatically scales throughput based on workload needs, up to 3 GiB/s for reads and 1 GiB/s for writes. Ideal for spiky or unpredictable workloads.[](https://aws.amazon.com/blogs/aws/new-announcing-amazon-efs-elastic-throughput/)
  - **Provisioned Throughput**: Allows you to specify throughput for predictable, high-performance workloads.[](https://aws.amazon.com/blogs/aws/new-announcing-amazon-efs-elastic-throughput/)
- **Storage Classes**:
  - **Standard**: SSD-powered for frequently accessed data with sub-millisecond latencies.
  - **Infrequent Access (IA)**: Cost-optimized for data accessed a few times per quarter, with low double-digit millisecond latencies.
  - **Archive**: For data accessed a few times a year, offering up to 50% lower storage costs than IA.[](https://aws.amazon.com/efs/faq/)
- **Security**: Supports encryption at rest and in transit, AWS Identity and Access Management (IAM) for access control, and VPC security groups for network access.[](https://docs.aws.amazon.com/efs/latest/ug/whatisefs.html)
- **Backup and Replication**: Integrates with AWS Backup for automated backups and supports EFS Replication for disaster recovery with low RPO and RTO.[](https://aws.amazon.com/efs/features/)

## Limitations
- **NFS Protocol Only**: EFS supports NFSv4.0 and NFSv4.1 but not Windows-based EC2 instances or system boot volumes.[](https://www.bmc.com/blogs/aws-efs-elastic-file-system/)[](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AmazonEFS.html)
- **Maximum File Size**: 47.9 TB per file system.[](https://www.geeksforgeeks.org/cloud-computing/introduction-to-aws-elastic-file-systemefs/)
- **Throughput and IOPS Limits**: Maximum throughput of 1000 MB/s and 16,000 IOPS per file system.[](https://www.geeksforgeeks.org/cloud-computing/introduction-to-aws-elastic-file-systemefs/)
- **Regional Restrictions**: Available in most AWS Regions, but some features (e.g., Elastic Throughput) are not available in AWS China Regions.[](https://aws.amazon.com/blogs/aws/new-announcing-amazon-efs-elastic-throughput/)

## Getting Started
1. **Create an EFS File System**:
   - Open the [Amazon EFS Management Console](https://console.aws.amazon.com/efs).
   - Click **Create file system**, provide a name, select a VPC, and choose default or custom settings (e.g., performance mode, throughput mode, encryption).
   - After creation, note the file system’s DNS name or mount target IPs.[](https://k21academy.com/amazon-web-services/amazon-elastic-file-system/)
2. **Install the EFS Client**:
   - On EC2 Linux instances, install the `amazon-efs-utils` package from AMI repositories or GitHub for supported distributions (e.g., Amazon Linux, Red Hat, Ubuntu).
   - For EC2 Mac instances running macOS (Big Sur, Monterey, Ventura, Sonoma, Sequoia), install via Homebrew from the `homebrew-aws` repository.[](https://docs.aws.amazon.com/efs/latest/ug/installing-amazon-efs-utils.html)
   - Example command for Amazon Linux:
     ```bash
     sudo yum install amazon-efs-utils
     ```
3. **Mount the File System**:
   - Create a mount target in your VPC for each AZ you want to access the file system from.
   - Use the `mount.efs` helper to mount the file system:
     ```bash
     sudo mount -t efs -o tls fs-12345678:/ /mnt/efs
     ```
   - Verify the mount:
     ```bash
     df -T /mnt/efs
     ```
   - For encryption in transit, ensure `stunnel` is updated, and for CloudWatch monitoring, install `botocore`.[](https://docs.aws.amazon.com/efs/latest/ug/installing-amazon-efs-utils.html)
4. **Configure Security**:
   - Set up IAM policies and VPC security groups to control access.
   - Enable encryption at rest during file system creation and encryption in transit during mounting.[](https://docs.aws.amazon.com/efs/latest/ug/whatisefs.html)
5. **Monitor and Optimize**:
   - Use CloudWatch to monitor metrics like `TotalIOBytes` and burst credit balance.
   - Enable lifecycle management to move infrequently accessed files to IA or Archive storage classes to reduce costs.[](https://github.com/aws-samples/amazon-efs-tutorial/blob/master/create-file-system/README.md)[](https://aws.amazon.com/blogs/aws/new-announcing-amazon-efs-elastic-throughput/)

## Example Use Cases
- **Shared Storage for Containers**: Use with ECS, EKS, or Fargate for persistent storage in containerized applications.[](https://docs.aws.amazon.com/eks/latest/userguide/efs-csi.html)
- **Big Data Analytics**: Leverage high throughput and scalability for analytics workloads.[](https://www.geeksforgeeks.org/cloud-computing/introduction-to-aws-elastic-file-systemefs/)
- **Content Management**: Host shared file systems for web servers or CMS platforms.[](https://aws.amazon.com/efs/features/)
- **Disaster Recovery**: Use EFS Replication to synchronize data across AZs or Regions.[](https://aws.amazon.com/efs/features/)

## Pricing
- **No Minimum Fees**: Pay only for storage, throughput, and read/write operations used.
- **Storage Costs**: Vary by storage class (e.g., Standard, IA, Archive). Example: $0.30/GB-month for Standard in US East (N. Virginia).[](https://aws.amazon.com/blogs/aws/amazon-elastic-file-system-production-ready-in-three-regions/)
- **Throughput Costs**: Elastic Throughput charges based on data transferred; Provisioned Throughput allows fixed pricing.
- **Free Tier**: New AWS customers get 5 GB of Standard storage with Regional file systems for 12 months. Starting July 15, 2025, up to $200 in Free Tier credits apply.[](https://aws.amazon.com/efs/pricing/)
- For detailed pricing, visit the [EFS Pricing page](https://aws.amazon.com/efs/pricing/).[](https://aws.amazon.com/efs/pricing/)



