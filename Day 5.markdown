# Cloud - DevOps Learning Journey - Day 5
**Date: 14.7.2025**

## Amazon EC2 Auto Scaling

Amazon EC2 Auto Scaling is a service that automatically adjusts the number of EC2 instances in a group based on application demand, ensuring optimal performance and cost efficiency. It supports horizontal scaling by adding (scaling out) or removing (scaling in) instances, making it ideal for dynamic workloads like web applications or batch processing.

### Key Concepts
- **Auto Scaling Group (ASG)**: A collection of EC2 instances managed as a unit, with defined minimum, maximum, and desired capacities.
- **Launch Template/Configuration**: Specifies instance details (e.g., AMI, instance type, security groups) for launching new instances.
- **Scaling Policies**:
  - **Target Tracking**: Maintains a target metric (e.g., 50% CPU utilization).
  - **Step Scaling**: Adjusts capacity in steps based on CloudWatch alarm thresholds.
  - **Simple Scaling**: Performs a single adjustment with a cooldown period.
  - **Predictive Scaling**: Uses ML to forecast and proactively adjust capacity.
  - **Scheduled Scaling**: Scales based on predictable schedules (e.g., business hours).
- **Health Checks**: Ensures instances are healthy using EC2 status checks or Elastic Load Balancer (ELB) health checks.
- **Integration**: Works with CloudWatch for monitoring, ELB for traffic distribution, and CloudFormation for automation.

### Benefits
- **Availability**: Distributes instances across Availability Zones (AZs) for fault tolerance.
- **Cost Efficiency**: Scales down during low demand and supports cost-effective instance types like Spot Instances.
- **Automation**: Simplifies instance management and application deployment.

### Setup Steps
1. **Create a Launch Template**:
   - Define the Amazon Machine Image (AMI), instance type (e.g., `t3.micro`), key pair, security groups, and storage.
   - Example: Use an Amazon Linux 2 AMI with a user data script to install a web server.
2. **Set Up an Auto Scaling Group**:
   - Specify the launch template, VPC, subnets (across multiple AZs), and capacity settings (e.g., min: 2, max: 10, desired: 4).
   - Enable ELB integration if distributing traffic.
3. **Configure Scaling Policies**:
   - Example: Set a target tracking policy to maintain 50% average CPU utilization.
   - Use CloudWatch to create alarms (e.g., scale out if CPU > 60% for 5 minutes).
4. **Enable Health Checks**:
   - Use ELB health checks for application-level monitoring or EC2 status checks for basic instance health.
5. **Monitor and Test**:
   - Use CloudWatch dashboards to track metrics like CPU, network, or request count.
   - Simulate load to test scaling behavior.

### Best Practices
- **Distribute Across AZs**: Deploy instances in multiple AZs for high availability.
- **Use Predictive Scaling**: Enable for workloads with predictable patterns (e.g., daily traffic spikes).
- **Optimize Costs**: Use Spot Instances for non-critical workloads and Savings Plans for consistent usage.
- **Set Notifications**: Configure SNS notifications for scaling events.
- **Test Health Checks**: Ensure ELB health checks detect application failures, not just instance status.
- **Leverage AWS Tools**: Use AWS Compute Optimizer for instance type recommendations and CloudFormation for infrastructure-as-code.

### Example Use Case
For a web application:
- Create an ASG with a minimum of 2 instances and a maximum of 8.
- Use a target tracking policy to maintain 50% CPU utilization.
- Integrate with an Application Load Balancer (ALB) to distribute traffic.
- Enable predictive scaling to handle peak shopping hours based on historical data.

### Pricing
- No additional cost for EC2 Auto Scaling.
- You pay for EC2 instances (On-Demand, Reserved, or Spot), EBS volumes, and CloudWatch monitoring fees.
- Tip: Use the AWS Pricing Calculator to estimate costs.

### Resources
- [AWS EC2 Auto Scaling Documentation](https://docs.aws.amazon.com/autoscaling/ec2/userguide/what-is-amazon-ec2-auto-scaling.html)
- [AWS Management Console](https://aws.amazon.com/console/) for hands-on setup.
- [AWS CLI Reference](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/autoscaling/index.html) for automation.
- Try the "Create your first Auto Scaling group" tutorial in the AWS Console.

### Next Steps
- Experiment with a simple ASG in your AWS account.
- Explore CloudWatch alarms and ELB integration.
- Learn about AWS CloudFormation for automated ASG deployments.

Happy learning on your Cloud - DevOps journey!