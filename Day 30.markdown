# Cloud DevOps Learning Journey - Day 30
*Date: August 8, 2025*

## Amazon EC2 Instance Store vs. Amazon Elastic Block Store (EBS)

Let’s break this down simply to understand the difference between **Amazon EC2 Instance Store** and **Amazon Elastic Block Store (EBS)**.

### 1. Amazon EC2 Instance Store
- **What it is**: Temporary storage physically attached to the host machine where your EC2 instance runs.
- **Data persistence**:  
  ❌ Data is lost if:
  - You stop the instance
  - The instance fails
  - You terminate the instance
- **Speed**: Very fast because it’s directly connected hardware.
- **Cost**: Included with the EC2 instance price (no extra cost).
- **Best for**:
  - Temporary data (e.g., caches, buffers, scratch data)
  - High-performance workloads that can tolerate data loss
- **Example use case**: Storing temporary files for a batch job that can be regenerated.

### 2. Amazon Elastic Block Store (EBS)
- **What it is**: Network-attached block storage that persists independently of the EC2 instance.
- **Data persistence**:  
  ✅ Data remains even if:
  - The instance is stopped
  - The instance is terminated (unless you choose delete-on-termination)
- **Speed**: Slower than instance store, but still fast and can be optimized (SSD, Provisioned IOPS, etc.).
- **Cost**: Charged separately based on GB per month + I/O requests.
- **Best for**:
  - Databases
  - Application data that must be saved
  - OS root volumes
- **Example use case**: Storing website files, database data, or logs that must survive instance restarts.

### Key Comparison Table
| Feature             | Instance Store            | EBS                          |
|---------------------|---------------------------|------------------------------|
| **Persistence**     | No                        | Yes                          |
| **Attached to**     | Physical host             | Network storage              |
| **Performance**     | Very high                 | High (configurable)          |
| **Cost**            | Included in EC2           | Separate charge              |
| **Data Loss**       | On stop/terminate/failure | Only if manually deleted     |
| **Use case**        | Temp, cache, scratch      | Databases, persistent storage|

### 💡 Quick way to remember:
- **Instance Store** = "Fast but forgetful" (temporary, tied to instance)
- **EBS** = "Persistent and portable" (survives instance changes)
