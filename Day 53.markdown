# Cloud devops learning journey-Day 53
Date:01.09.2025

## Overview
Amazon CloudWatch is a monitoring and observability service provided by Amazon Web Services (AWS). It enables users to collect and track metrics, monitor log files, set alarms, and automatically react to changes in AWS resources. CloudWatch provides real-time insights into the operational health, performance, and resource utilization of AWS infrastructure and applications. It is designed for developers, DevOps engineers, site reliability engineers (SREs), and IT managers to ensure optimal performance and reliability.

## Key Features
- **Metrics Collection**: Collects and stores metrics from AWS services (e.g., EC2, S3, RDS) and custom metrics from applications. Metrics are time-ordered data points stored in namespaces (e.g., AWS/EC2).[](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/cloudwatch_concepts.html)
- **Logs Monitoring**: Centralizes logs from EC2 instances, CloudTrail, Route 53, and other sources, enabling storage, search, and analysis in CloudWatch Logs.[](https://www.pulumi.com/docs/iac/clouds/aws/guides/cloudwatch/)
- **Alarms and Automation**: Set alarms to trigger notifications (via SNS) or actions (e.g., EC2 instance stop/start) based on metric thresholds. Supports automated responses to performance changes.[](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/cloudwatch_architecture.html)
- **Dashboards**: Create customizable dashboards to visualize metrics, logs, and alarms with widgets like line graphs, stacked area graphs, and text.[](https://cloudfoundation.com/blog/what-is-amazon-cloudwatch/)
- **CloudWatch Agent**: Collects system-level metrics and logs from EC2 instances and on-premises servers. Supports StatsD and collectd protocols for custom metrics.[](https://github.com/aws/amazon-cloudwatch-agent)
- **EventBridge Integration**: Monitors events and triggers actions (e.g., Lambda functions, SNS topics) for real-time responses to state changes.[](https://aws.amazon.com/blogs/storage/amazon-cloudwatch-events-and-metrics-for-aws-backup/)
- **Cross-Account and Cross-Region**: Aggregates metrics and logs across multiple AWS accounts and regions for unified monitoring.[](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/cloudwatch_architecture.html)

## Setup Instructions
1. **Access CloudWatch**:
   - Navigate to the AWS Management Console and select CloudWatch.
   - Alternatively, use the AWS CLI or SDKs for programmatic access.

2. **Install CloudWatch Agent**:
   - Download the agent package for your operating system (e.g., Amazon Linux 2023, Windows Server) using the appropriate S3 link (e.g., `https://amazoncloudwatch-agent.s3.amazonaws.com/amazon_linux/amd64/latest/amazon-cloudwatch-agent.rpm`). Ensure your connection uses TLS 1.2 or later.[](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/download-CloudWatch-Agent-on-EC2-Instance-commandline-first.html)
   - Install the agent using the command line. For Amazon Linux:
     ```bash
     sudo rpm -U ./amazon-cloudwatch-agent.rpm
     ```
   - Attach the `CloudWatchAgentServerPolicy` IAM role to the instance.

3. **Create Configuration File**:
   - Use the CloudWatch agent configuration wizard (`amazon-cloudwatch-agent-config-wizard`) to generate a JSON configuration file interactively.[](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/create-cloudwatch-agent-configuration-file-wizard.html)
   - Alternatively, manually create a JSON file with sections for agent, metrics, logs, and traces. Example:
     ```json
     {
       "agent": {
         "metrics_collection_interval": 60,
         "region": "us-east-1"
       },
       "metrics": {
         "metrics_collected": {
           "cpu": {
             "measurement": ["usage_active"],
             "totalcpu": true
           },
           "mem": {
             "measurement": ["used_percent"]
           }
         }
       },
       "logs": {
         "logs_collected": {
           "files": {
             "collect_list": [
               {
                 "file_path": "/var/log/messages",
                 "log_group_name": "/var/log/messages"
               }
             ]
           }
         }
       }
     }
     ```
   - Store the file locally (e.g., `/opt/aws/amazon-cloudwatch-agent/bin/config.json` on Linux) or in Systems Manager Parameter Store.[](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch-Agent-Configuration-File-Details.html)[](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/create-cloudwatch-agent-configuration-file-wizard.html)

4. **Start the Agent**:
   - Run the agent with the configuration file:
     ```bash
     /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl -a fetch-config -m ec2 -s -c file:/opt/aws/amazon-cloudwatch-agent/bin/config.json
     ```
   - Restart the agent after configuration changes.[](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/create-cloudwatch-agent-configuration-file.html)

5. **Set Up Alarms**:
   - In the CloudWatch console, navigate to "Alarms" and click "Create Alarm."
   - Select a metric (e.g., CPUUtilization for an EC2 instance), define the threshold (e.g., >80% for 5 minutes), and configure actions (e.g., SNS notification).[](https://www.billgist.com/blog/mastering-monitoring-an-in-depth-guide-to-amazon-cloudwatch-1lj7/)

6. **Create Dashboards**:
   - In the CloudWatch console, go to "Dashboards" and create a new dashboard.
   - Add widgets (e.g., line graphs, text) to visualize metrics and logs. Use Markdown for text widgets to format tables or buttons.[](https://docs.aws.amazon.com/awsconsolehelpdocs/latest/gsg/aws-markdown.html)[](https://cloudfoundation.com/blog/what-is-amazon-cloudwatch/)

## Additional Resources
- **AWS Documentation**: [Amazon CloudWatch User Guide](https://docs.aws.amazon.com/cloudwatch/)[](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/cloudwatch_architecture.html)
- **Pricing**: See [Amazon CloudWatch Pricing](https://aws.amazon.com/cloudwatch/pricing/) for details on metrics, logs, and traces costs.[](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch-Agent-Configuration-File-Details.html)
- **Release Notes**: Check the latest CloudWatch Agent updates at [GitHub RELEASE_NOTES](https://github.com/aws/amazon-cloudwatch-agent/blob/main/RELEASE_NOTES).[](https://github.com/aws/amazon-cloudwatch-agent/blob/main/RELEASE_NOTES)
- **Tutorials**: Explore [CloudWatch Tutorials](https://aws.amazon.com/cloudwatch/getting-started/) for hands-on guides.

## Notes
- Metrics are retained for up to 15 days by default, with high-resolution metrics (sub-60 seconds) retained for 3 hours.[](https://cloudfoundation.com/blog/what-is-amazon-cloudwatch/)
- Ensure IAM roles have appropriate permissions (e.g., `CloudWatchAgentServerPolicy`, `AmazonS3ReadOnlyAccess`) for agent operations.[](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/download-CloudWatch-Agent-on-EC2-Instance-commandline-first.html)
- Use CloudWatch Logs Insights for advanced log analysis and EventBridge for event-driven automation.[](https://www.pulumi.com/docs/iac/clouds/aws/guides/cloudwatch/)[](https://aws.amazon.com/blogs/storage/amazon-cloudwatch-events-and-metrics-for-aws-backup/)