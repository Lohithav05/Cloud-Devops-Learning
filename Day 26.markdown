# Cloud DevOps Learning Journey: Day 26 
**Date**: August 4, 2025

## Overview
Welcome to Day 26 of the Cloud DevOps Learning Journey! Today, we dive into **Amazon CloudFront** and the **Amazon Global Network**, exploring how these AWS services enhance content delivery and support scalable, high-performance applications in a DevOps environment.

## Topics Covered
### 1. Amazon CloudFront
Amazon CloudFront is a fast, scalable, and secure **Content Delivery Network (CDN)** provided by AWS. It delivers data, videos, applications, and APIs to users globally with low latency and high transfer speeds.

- **Key Features**:
  - **Edge Locations**: CloudFront uses a global network of edge locations to cache content closer to users, reducing latency. As of 2025, CloudFront has over 51 edge locations worldwide, including points of presence (POPs) in cities like Beijing, Shanghai, Zhongwei, and Shenzhen for CloudFront China.[](https://www.amazonaws.cn/en/cloudfront/features/)
  - **Performance**: Leverages the AWS global network backbone for efficient data transfer between edge locations and AWS services.
  - **Security**: Integrates with AWS Shield for DDoS protection, AWS WAF for web application security, and supports HTTPS for secure data transfer.
  - **DevOps-Friendly**: Offers APIs, SDKs, and integration with Infrastructure as Code (IaC) tools like AWS CloudFormation for automated deployment and management.[](https://www.amazonaws.cn/en/cloudfront/features/)
  - **Customizable Behaviors**: Allows configuration of cache behaviors, device detection, and compression modes to optimize content delivery.

- **Use Case**: Serve static assets (e.g., images, videos) or dynamic content (e.g., APIs) with low latency, ideal for web applications, streaming services, or global e-commerce platforms.

### 2. AWS Global Accelerator

AWS Global Accelerator is a networking service that improves the performance and availability of applications by routing user traffic through the AWS global network to the nearest endpoint.
**Key Feature**:
-**Global Traffic Routing**: Directs user traffic to the closest AWS endpoint (e.g., Application Load Balancers, EC2 instances, or Elastic IPs) using the AWS global network, reducing latency and improving reliability.
-**Static IP Addresses**: Provides two static anycast IP addresses for consistent application access.
**Performance**: Uses the AWS global network to avoid internet congestion, ensuring faster and more reliable connections.
-**Health Checks**: Automatically routes traffic to healthy endpoints, enhancing fault tolerance.
DevOps Integration: Supports automation via AWS CLI, SDKs, or IaC tools for managing accelerator configurations

-**Use Case**: Optimizes performance for latency-sensitive applications like gaming, VoIP, or real-time data services, especially in multi-region deployments.




