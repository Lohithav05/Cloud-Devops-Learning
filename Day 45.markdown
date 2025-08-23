# Cloud devops learning journey-Day 45
Date:23.08.2025

This README provides an overview of three AWS services—Amazon DocumentDB, AWS Backup, and Amazon Neptune—focusing on their key features, use cases, and integration for modern database workloads and data protection. Last updated: August 23, 2025.

## Amazon DocumentDB (with MongoDB Compatibility)

### Overview
Amazon DocumentDB is a fully managed, MongoDB-compatible document database designed for scalability, high availability, and performance. It supports MongoDB 3.6 and 4.0 APIs, enabling seamless migration of existing MongoDB applications.

### Key Features
- **Scalability**: Elastic Clusters for horizontal scaling; serverless option adjusts capacity automatically, reducing costs by up to 90%.
- **High Availability**: Replicates data across multiple Availability Zones (AZs); Global Clusters support low-latency reads in up to five AWS Regions.
- **Backups**: Automated backups with point-in-time recovery (PITR) up to 35 days. Manual snapshots stored in Amazon S3, shareable across accounts.
- **Security**: Encryption at rest with AWS KMS; IAM-based access control.
- **Integration**: Supports Amazon OpenSearch Service, Amazon CloudWatch, and AWS Backup.

### Use Cases
- Content management (e.g., menus, reviews, photos).
- User profile management for personalized recommendations.
- Mobile/web apps requiring fast JSON data access.

### Getting Started
- Create a cluster: `aws docdb describe-db-clusters --filter Name=engine,Values=docdb`.
- Migrate MongoDB workloads using AWS Database Migration Service (DMS) or `mongodump`/`mongorestore`.
- Docs: [Amazon DocumentDB](https://aws.amazon.com/documentdb/)

## AWS Backup

### Overview
AWS Backup is a fully managed, centralized backup service for protecting data across AWS services, including databases like Amazon DocumentDB and Amazon Neptune.

### Key Features
- **Centralized Management**: Manage backups for multiple AWS services (e.g., DocumentDB, Neptune, RDS, EBS) via a single console.
- **Automation**: Schedule backups with customizable policies; supports cross-region and cross-account backup copying.
- **Restore**: Point-in-time recovery for supported databases; granular restore for files and volumes.
- **Security**: Encryption with AWS KMS; compliance with HIPAA, GDPR, and SOC.
- **Monitoring**: Integration with Amazon CloudWatch for backup job tracking.

### Use Cases
- Protecting database workloads (e.g., DocumentDB, Neptune) against data loss.
- Automating compliance-driven backup schedules.
- Disaster recovery across regions or accounts.

### Getting Started
- Create a backup plan: `aws backup create-backup-plan`.
- Assign resources using tags or resource ARNs.
- Docs: [AWS Backup](https://aws.amazon.com/backup/)

## Amazon Neptune

### Overview
Amazon Neptune is a fully managed graph database service optimized for storing and querying highly connected data, supporting Property Graph and RDF models.

### Key Features
- **Graph Models**: Supports Apache TinkerPop Gremlin and W3C SPARQL for Property Graph and RDF queries.
- **Performance**: Fast queries for complex relationships; scales to billions of relationships.
- **High Availability**: Replicas across multiple AZs; automated backups with PITR up to 35 days.
- **Security**: Encryption at rest and in transit; VPC and IAM integration.
- **Integration**: Supports AWS Lambda, Amazon OpenSearch Service, and AWS Glue for analytics.

### Use Cases
- Knowledge graphs for recommendation engines.
- Social networking applications analyzing relationships.
- Fraud detection by identifying patterns in connected data.

