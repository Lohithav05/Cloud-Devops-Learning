# Cloud devops learning journey-Day 57
Date:05.09.2025

This README provides an overview of AWS Support Plans, AWS Marketplace, and strategies for cost optimization based on the latest available information as of September 5, 2025. It is intended to help users understand the options available for support, marketplace offerings, and cost-saving techniques when using Amazon Web Services (AWS).

## AWS Support Plans

AWS offers a range of support plans tailored to different customer needs, from basic account assistance to enterprise-level technical support. Below is a summary of the available plans:

### 1. Basic Support
- **Cost**: Free, included with all AWS accounts.
- **Features**:
  - 24/7 access to customer service for billing and account inquiries.
  - Access to AWS documentation, whitepapers, and AWS re:Post.
  - Limited access to AWS Trusted Advisor for basic checks.
- **Best For**: Individuals or small businesses with minimal technical support needs.

### 2. Developer Support
- **Cost**: Starts at $29/month or 3% of monthly AWS usage (whichever is higher).
- **Features**:
  - All Basic Support features.
  - Technical support via email during business hours with a 12-hour response time for general issues.
  - Access to AWS Trusted Advisor for core checks to optimize performance and security.
- **Best For**: Developers building cloud-native applications with moderate support needs.

### 3. Business Support
- **Cost**: Starts at $100/month or 10% of monthly AWS usage (lower percentages for higher usage tiers).
- **Features**:
  - All Developer Support features.
  - 24/7 technical support via phone, chat, and web with a 1-hour response time for production system issues.
  - Full access to AWS Trusted Advisor for cost optimization, security, and performance recommendations.
  - AWS Infrastructure Event Management for planned events.
- **Best For**: Businesses running production workloads needing faster response times and optimization guidance.

### 4. Enterprise On-Ramp Support
- **Cost**: Starts at $5,500/month (based on usage tiers).
- **Features**:
  - All Business Support features.
  - Access to a pool of Technical Account Managers (TAMs) for proactive guidance.
  - 30-minute response time for business-critical system issues.
  - AWS Incident Detection and Response for proactive incident management.
- **Best For**: Medium to large businesses with critical workloads requiring rapid support and optimization.

### 5. Enterprise Support
- **Cost**: Starts at $15,000/month.
- **Features**:
  - All Enterprise On-Ramp features.
  - Dedicated Technical Account Manager (TAM) for personalized guidance.
  - 15-minute response time for mission-critical system issues.
  - Strategic Business Reviews, Cost-Optimization Workshops, and Well-Architected Reviews.
  - AWS Countdown Premium (additional fee) for migrations, modernizations, and go-live events.
- **Best For**: Large enterprises with mission-critical workloads needing comprehensive support.

**Note**: Support plan costs are calculated based on gross AWS charges (before discounts or credits) for certain services. Charges for AWS Support, AWS Marketplace, and other specific services are excluded from the fee calculation. For detailed pricing, refer to the AWS Support Pricing page: https://aws.amazon.com/support/plans/.[](https://aws.amazon.com/premiumsupport/pricing/)

## AWS Marketplace

AWS Marketplace is a digital catalog where customers can find, buy, and deploy software and services that run on AWS. It simplifies procurement and integration for businesses.

### Key Features
- **Software Offerings**: Includes infrastructure software, business applications, and machine learning solutions from third-party vendors and AWS partners.
- **Pricing Models**:
  - Pay-as-you-go, subscriptions, or contract-based pricing.
  - Some offerings are free or include free trials.
  - Costs for Bedrock Marketplace purchases are billed as Bedrock usage, though visible through AWS Marketplace.[](https://aws.amazon.com/premiumsupport/pricing/)
- **Benefits**:
  - Streamlined procurement with consolidated billing through AWS.
  - Access to pre-configured software for quick deployment.
  - Support for private offers and custom pricing through AWS Marketplace Private Offers.
- **Use Cases**:
  - Deploying security tools, DevOps solutions, or AI/ML models.
  - Accessing specialized software for industries like healthcare or finance.

**Note**: AWS Marketplace purchases are managed through the AWS Management Console, and costs are included in your AWS bill. For more details, visit: https://aws.amazon.com/marketplace/.

## Cost Optimization Strategies

AWS provides tools and pricing models to help optimize cloud spending while maintaining performance and scalability. Below are key strategies and tools for cost optimization:

### 1. AWS Pricing Models
- **On-Demand Pricing**: Pay for resources as used, ideal for unpredictable workloads but more expensive.
- **Savings Plans**: Commit to a consistent usage amount (measured in $/hour) for 1 or 3 years to save up to 72% compared to On-Demand pricing. Types include:
  - Compute Savings Plans: Flexible across EC2, Fargate, and Lambda, saving up to 66%.[](https://aws.amazon.com/savingsplans/compute-pricing/)
  - EC2 Instance Savings Plans: Specific to EC2 instances, higher savings for specific instance families.
  - SageMaker Savings Plans: For machine learning workloads.
- **Reserved Instances (RIs)**: Commit to specific instance types for 1 or 3 years for up to 72% savings. Convertible RIs allow instance family changes but cannot be sold in the RI Marketplace.[](https://spot.io/resources/aws-cost-optimization/aws-cost-savings-12-great-ways-to-save-on-aws/)
- **Spot Instances**: Use spare EC2 capacity for up to 90% savings, ideal for fault-tolerant workloads but subject to termination with 2-minute notice.[](https://spot.io/resources/aws-cost-optimization/aws-cost-savings-12-great-ways-to-save-on-aws/)
- **Free Tier**: Offers limited free usage for new AWS customers for the first year.[](https://spot.io/resources/aws-pricing/5-models-pricing-for-10-popular-aws-services/)

### 2. AWS Cost Management Tools
- **AWS Cost Explorer**: Visualize and analyze spending trends, forecast costs, and identify savings opportunities.[](https://n2ws.com/blog/aws-cost-optimization/understanding-aws-costs)
- **AWS Budgets**: Set custom spending thresholds and receive alerts for overages.[](https://n2ws.com/blog/aws-cost-optimization/understanding-aws-costs)
- **AWS Trusted Advisor**: Provides recommendations for cost optimization, such as identifying idle resources, underutilized instances, or Savings Plans opportunities.[](https://docs.aws.amazon.com/awssupport/latest/user/cost-optimization-checks.html)
- **AWS Compute Optimizer**: Uses machine learning to recommend optimal instance sizes and types based on usage patterns.[](https://n2ws.com/blog/aws-cost-optimization/understanding-aws-costs)
- **AWS Pricing Calculator**: Estimate costs for planned workloads and compare pricing models: https://calculator.aws/.[](https://calculator.aws/)

### 3. Practical Cost Optimization Tips
- **Right-Sizing Resources**: Use AWS Compute Optimizer to downsize over-provisioned instances or switch to cost-effective instance types.[](https://n2ws.com/blog/aws-cost-optimization/understanding-aws-costs)
- **Auto-Scaling**: Implement auto-scaling for services like EC2 and DynamoDB to match resource usage to demand.[](https://aws.amazon.com/premiumsupport/support-cloud-cost-optimization/)
- **Delete Idle Resources**: Use Trusted Advisor to identify and remove unused Elastic IP addresses, unattached EBS volumes, or idle load balancers.[](https://n2ws.com/blog/aws-cost-optimization/understanding-aws-costs)
- **Leverage Spot Instances for Non-Critical Workloads**: Use Spot Instances for batch processing or testing environments to reduce costs.[](https://spot.io/resources/aws-cost-optimization/aws-cost-savings-12-great-ways-to-save-on-aws/)
- **Monitor and Optimize Data Transfer Costs**: Analyze data transfer costs using AWS Cost Explorer and minimize cross-region or internet data transfers.[](https://docs.aws.amazon.com/whitepapers/latest/how-aws-pricing-works/aws-cost-optimization.html)
- **Use AWS Organizations**: Consolidate accounts for better cost tracking, but note that support plan costs are billed per account with a $100 minimum for Business Support.[](https://on-promise.cloud/en/compendium/09-AWS-support-cost.html)

### 4. Enterprise Discount Program (EDP)
- **Overview**: Offers customized discounts and enhanced support for organizations with significant AWS usage.
- **Benefits**: Includes faster response times, dedicated TAMs, and cost optimization workshops to reduce risks and improve efficiency.
- **Considerations**: Negotiated based on projected usage and growth, ideal for large enterprises.[](https://on-promise.cloud/en/compendium/09-AWS-support-cost.html)

