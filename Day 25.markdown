# Cloud DevOps Learning Journey: Day 25
*Date: August 3, 2025*

## Overview
On Day 25 of my Cloud DevOps learning journey, I explored the fundamentals of networking, a critical component for building and managing cloud-based systems. Understanding networking concepts is essential for configuring secure, scalable, and efficient cloud infrastructure.

## Topics Covered
- **Networking Basics**:
  - **IP Addressing**: Learned about IPv4 and IPv6, including private and public IP ranges.
  - **Subnets and CIDR**: Understood how subnets divide networks and how CIDR notation (e.g., /24) defines network boundaries.
  - **DNS**: Explored Domain Name System (DNS) for translating domain names to IP addresses.
  - **Ports and Protocols**: Studied common ports (e.g., 80 for HTTP, 443 for HTTPS) and protocols (TCP, UDP).
  - **Firewalls and Security Groups**: Learned how firewalls and cloud security groups control inbound and outbound traffic.
  - **Load Balancers**: Understood how load balancers distribute traffic across multiple servers for scalability and reliability.
  - **VPCs (Virtual Private Clouds)**: Explored the concept of VPCs for isolating cloud resources in a private network.

## Key Learnings
- Configured a basic VPC with public and private subnets in a cloud provider (e.g., AWS, Azure, or GCP).
- Set up security groups to allow specific traffic (e.g., HTTP on port 80) while restricting others.
- Practiced resolving DNS queries and understanding latency impacts.
- Experimented with a simple load balancer setup to distribute traffic across two mock instances.

## Tools Used
- **Cloud Provider**: AWS (or specify your chosen provider, e.g., Azure, GCP)
- **CLI Tools**: AWS CLI, Terraform (optional for infrastructure as code)
- **Network Utilities**: `ping`, `traceroute`, `nslookup` for troubleshooting

## Challenges
- Configuring subnet masks correctly to avoid IP conflicts.
- Understanding the difference between stateful and stateless firewalls.
- Debugging DNS resolution issues during setup.

## Next Steps
- Dive deeper into advanced networking topics like VPNs and Direct Connect.
- Explore network monitoring tools (e.g., CloudWatch, Prometheus).
- Set up a multi-tier architecture with a load balancer and auto-scaling group.

## Resources
- [AWS Networking Fundamentals](https://aws.amazon.com/vpc/)
- [Terraform VPC Module](https://registry.terraform.io/modules/terraform-aws-modules/vpc/aws/latest)
- [Networking Basics - Cisco](https://www.cisco.com/c/en/us/solutions/enterprise-networks/what-is-networking.html)
