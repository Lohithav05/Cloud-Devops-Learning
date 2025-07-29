# Cloud DevOps Learning Journey - Day 20
**Date**: July 29, 2025

## Topics Covered
1. **Network ACL (Access Control List)**  
   - Overview: Network ACLs are stateless, layer 4 firewalls in cloud environments (e.g., AWS) that control traffic at the subnet level.  
   - Purpose: Filters inbound and outbound traffic based on rules to enhance network security.  

2. **Network ACL Default**  
   - Default Behavior: In AWS, every VPC comes with a default Network ACL that allows all inbound and outbound traffic.  
   - Configuration: Can be modified to restrict traffic but cannot be deleted.  

3. **Network ACL with Custom Rules**  
   - Custom Rules: Create rules to allow or deny specific traffic based on protocol, port range, source/destination IP, etc.  
   - Rule Numbering: Rules are evaluated in ascending order (e.g., rule 100 is checked before rule 200).  
   - Best Practice: Explicitly define allow/deny rules and include a default deny rule for unlisted traffic.  

4. **Stateless Packet Filtering**  
   - Stateless Nature: Network ACLs do not track connection states; both inbound and outbound traffic must have explicit rules.  
   - Example: To allow HTTP traffic (port 80), you need rules for both incoming requests and outgoing responses.  
   - Comparison: Unlike security groups (stateful), Network ACLs require rules for both directions of traffic.  

## Key Takeaways
- Network ACLs provide subnet-level security