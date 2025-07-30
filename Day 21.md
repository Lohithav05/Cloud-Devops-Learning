# Cloud DevOps Learning Journey - Day 21 
**Date**: July 30, 2025

## Overview
On Day 21 of my Cloud DevOps learning journey, I explored **AWS Security Groups**, a critical component of network security in AWS cloud infrastructure. Security Groups act as virtual firewalls to control inbound and outbound traffic for EC2 instances and other AWS resources. Below is a summary of the topics covered and key takeaways.

## Topics Covered
1. **Default Security Group**
   - Each AWS VPC includes a default security group automatically assigned to resources unless a custom group is specified.
   - By default, allows all outbound traffic and denies all inbound traffic unless explicitly configured.
   - Best practice: Avoid relying on the default security group for production workloads; create custom groups for better control and security.

2. **Custom Security Groups**
   - Learned to create and configure custom security groups in AWS to define specific traffic rules for applications or services.
   - Rules specify protocols (e.g., TCP, UDP), port ranges, and source/destination (e.g., IP ranges, other security groups).
   - Emphasized the principle of least privilege: Only allow necessary traffic (e.g., HTTP on port 80 for web servers) to minimize security risks.

3. **Stateful Packet Filtering**
   - Understood that AWS Security Groups are stateful, meaning they automatically allow return traffic for established connections.
   - For example, if an inbound rule allows TCP traffic on port 80, the response traffic is permitted without needing an explicit outbound rule.
   - Compared stateful Security Groups with stateless Network ACLs to understand their complementary roles in AWS VPC security.



