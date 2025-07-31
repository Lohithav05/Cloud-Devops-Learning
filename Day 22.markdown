# Cloud DevOps Learning Journey: Day 22
**Date: 31 July 2025**

## Overview
On Day 22 of my Cloud DevOps learning journey, I delved deeper into AWS networking concepts, focusing on securing and configuring network environments within Amazon Virtual Private Cloud (VPC). The day was split between understanding the theoretical differences between Network Access Control Lists (ACLs) and Security Groups, and applying practical knowledge through a hands-on Amazon VPC demo. Below is a detailed breakdown of the topics covered.

## Topics Covered

### 1. Difference Between Network ACLs and Security Groups
This section explored the fundamental differences between Network ACLs and Security Groups, two critical AWS tools for controlling network traffic. Key points include:

- **Network ACLs**:
  - Operate at the **subnet level**, controlling traffic entering and leaving a subnet.
  - **Stateless**: Rules must explicitly allow both inbound and outbound traffic (e.g., a request and its response require separate rules).
  - Rules are evaluated in **numerical order** (lowest to highest), with an implicit "deny all" rule at the end.
  - Support both **allow** and **deny** rules, providing granular control.
  - Use case: Broad traffic filtering for entire subnets, such as blocking specific IP ranges or protocols.

- **Security Groups**:
  - Operate at the **instance level** (e.g., EC2 instances, RDS databases), controlling traffic to and from specific resources.
  - **Stateful**: Automatically allow return traffic for allowed inbound requests (e.g., a response to an HTTP request is permitted without an explicit outbound rule).
  - Only support **allow** rules; deny rules are not available.
  - Rules are evaluated **collectively**, with no specific order.
  - Use case: Fine-tuned access control for individual resources, such as allowing SSH access from a specific IP.

- **Key Differences**:
  - **Scope**: Network ACLs apply to subnets, while Security Groups apply to instances.
  - **State**: Network ACLs are stateless; Security Groups are stateful.
  - **Rule Types**: Network ACLs support allow/deny; Security Groups only support allow.
  - **Order of Execution**: Network ACLs are processed before Security Groups in the traffic flow.
  - **Use Together**: Combine both for layered security (e.g., Network ACLs for subnet-level restrictions, Security Groups for instance-specific rules).

- **Learning Outcome**: Understood how to strategically use Network ACLs and Security Groups to implement a defense-in-depth approach for securing AWS resources.

### 2. Amazon VPC Demo
In this hands-on session, I created and configured an Amazon VPC from scratch to solidify my understanding of AWS networking. The demo covered the following steps:

- **VPC Creation**:
  - Created a new VPC with a CIDR block (e.g., `10.0.0.0/16`) to define the IP address range.
  - Configured the VPC to support both IPv4 and IPv6 for future-proofing.

- **Subnet Setup**:
  - Created **public** and **private subnets** across multiple Availability Zones (e.g., `10.0.1.0/24` for public, `10.0.2.0/24` for private).
  - Associated subnets with appropriate route tables to control traffic flow.

- **Internet Gateway**:
  - Attached an Internet Gateway to the VPC to enable communication with the internet.
  - Updated the public subnet’s route table to include a route to the Internet Gateway (`0.0.0.0/0`).

- **Route Tables**:
  - Configured a public route table with routes to the Internet Gateway.
  - Created a private route table for internal traffic, ensuring no direct internet access for private subnets.

- **Security Configurations**:
  - Set up a **Security Group** to allow HTTP (port 80) and SSH (port 22) access to an EC2 instance in the public subnet, restricting SSH to a specific IP range.
  - Configured a **Network ACL** to allow HTTP/HTTPS traffic to the public subnet while blocking unwanted protocols (e.g., FTP).

- **Testing**:
  - Launched an EC2 instance in the public subnet and verified connectivity using SSH and HTTP.
  - Simulated a private subnet scenario by launching an instance without public access, confirming isolation.

- **Learning Outcome**: Gained practical experience in designing a secure, scalable VPC architecture, including subnet segmentation, routing, and access control. Understood the interplay between VPC components and security mechanisms.

## Key Takeaways
- Network ACLs and Security Groups serve complementary roles in AWS network security, with ACLs providing subnet-level control and Security Groups offering instance-level precision.
- A well-architected VPC requires careful planning of CIDR blocks, subnets, and routing to ensure scalability and security.
- Hands-on practice with VPC configuration reinforces theoretical knowledge and builds confidence in managing cloud network environments.

## Next Steps
- Explore advanced VPC features, such as VPC Peering, Transit Gateways, and VPC Endpoints.
- Dive into automating VPC setup using Infrastructure as Code (IaC) tools like AWS CloudFormation or Terraform.
- Study AWS NAT Gateway and Bastion Hosts for secure access to private subnets.