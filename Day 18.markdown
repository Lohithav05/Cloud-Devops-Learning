# Cloud DevOps Learning Journey: Day 18
**Date**: July 27, 2025  


## Overview
On Day 18 of my Cloud DevOps learning journey, I explored the fundamentals of networking in the cloud, focusing on subnets. I learned how subnets segment networks, the differences between private and public subnets, and their roles in building secure and scalable cloud architectures.

## Subnets
- **Definition**: A subnet is a subdivided portion of a network that allows for better organization, security, and management of resources in a cloud environment.
- **Purpose**: Enables segmentation of a Virtual Private Cloud (VPC) to control traffic flow, improve security, and optimize resource allocation.
- **Key Learning**: Subnets are tied to specific Availability Zones (AZs) and defined by a CIDR block (e.g., 10.0.1.0/24).

## Public Subnets
- **Definition**: Subnets with a route to the internet via an Internet Gateway, allowing resources to communicate with the public internet.
- **Use Cases**:
  - Hosting web servers, APIs, or load balancers (e.g., AWS Elastic Load Balancer).
  - Resources requiring outbound internet access (e.g., for software updates).
- **Key Learning**: Public subnets require a route table with a 0.0.0.0/0 route to an Internet Gateway.

## Private Subnets
- **Definition**: Subnets without direct internet access, designed for resources that need isolation from the public internet.
- **Use Cases**:
  - Hosting databases, application servers, or backend services (e.g., RDS instances).
  - Enhancing security for sensitive workloads.
- **Key Learning**: Private subnets use NAT Gateways or NAT Instances in a public subnet for controlled outbound internet access.

## Key Takeaways
- Subnets are critical for organizing cloud networks and enforcing security boundaries.
- Public subnets enable internet-facing services, while private subnets protect sensitive resources.
- Understanding route tables and gateways is essential for configuring subnet connectivity.

