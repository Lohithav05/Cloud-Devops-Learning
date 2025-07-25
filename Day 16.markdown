# Cloud DevOps Learning Journey: Day 16
**Date: 25.7.2025**

## 📦 1. Amazon VPC (Virtual Private Cloud)

**Definition:**  
A VPC is like your own private data center inside AWS.

**You can:**  
* Launch AWS resources (like EC2) in your isolated network  
* Control IP address ranges, subnets, route tables, and firewalls  

**Think of it like:**  
A fenced compound where you place your buildings (servers), and control who can come in/out.

## 🧱 2. Subnets

**Definition:**  
Subnets are subdivisions of a VPC where you group resources based on access type:  

* **Public Subnet** – Accessible from the internet (usually for web servers)  
* **Private Subnet** – No direct internet access (used for databases, backend servers)  

**Think of it like:**  
Rooms inside your compound. Some rooms (public) have windows/doors to the outside world, others (private) don't.

## 🔌 3. AWS Direct Connect

**Definition:**  
A dedicated physical connection between your on-premises data center and AWS cloud.  

* High-speed (up to 100 Gbps)  
* Lower latency than internet VPN  
* More secure and reliable  

**Use case:**  
Ideal for companies needing constant, secure, high-performance connections to AWS.  

**Think of it like:**  
A private leased line from your office to AWS — faster and safer than public internet.

## 🛡️ 4. Virtual Private Gateway (VGW)

**Definition:**  
A gateway attached to your VPC to enable VPN or Direct Connect connections from outside AWS.  

* Used for site-to-site VPNs and Direct Connect  
* It connects your VPC to remote networks  

**Think of it like:**  
A security gate at your compound that lets verified outsiders (on-prem systems) enter.

## 🌐 5. Virtual Private Network (VPN)

**Definition:**  
A secure tunnel over the internet that connects your on-premise network to your AWS VPC.  

* Uses IPSec for encryption  
* Setup with Virtual Private Gateway on AWS side  

**Types:**  
* **Site-to-site VPN** (connects entire office network to VPC)  
* **Client VPN** (connects a user's laptop to VPC)  

**Think of it like:**  
A secure tunnel that lets your office computers safely talk to AWS services over the internet.