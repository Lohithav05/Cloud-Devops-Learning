#  Cloud DevOps Learning Journey -Day 10
Date:19.7.2025

## Topics Covered
On Day 10 of my Cloud DevOps learning journey, I explored key AWS services and concepts related to containers and serverless computing. Below is a summary of the topics I studied:

### 1. **Creating AWS Lambda**
- Learned about AWS Lambda, a serverless computing service that allows running code without provisioning or managing servers.
- Explored how to create a Lambda function using the AWS Management Console, CLI, or SDK.
- Understood key components: function code, runtime, triggers (e.g., API Gateway, S3 events), and IAM roles for permissions.
- Practiced creating a simple Lambda function to process an event and return a response.

### 2. **Containers**
- Studied the basics of containers: lightweight, portable units that package code and dependencies.
- Learned about Docker as a containerization platform and its role in modern DevOps.
- Explored container images, containers, and the Docker Hub for storing and sharing images.

### 3. **Amazon ECS (Elastic Container Service)**
- Explored Amazon ECS, a fully managed container orchestration service.
- Learned about ECS clusters, tasks, and services.
- Understood how ECS integrates with other AWS services like ELB (Elastic Load Balancer) and IAM.
- Studied task definitions to specify container images, CPU, memory, and networking requirements.

### 4. **Amazon EKS (Elastic Kubernetes Service)**
- Learned about Amazon EKS, a managed Kubernetes service for running containerized workloads.
- Explored Kubernetes concepts: pods, deployments, services, and namespaces.
- Understood how EKS simplifies cluster management by handling control plane operations.
- Studied the process of creating an EKS cluster and deploying applications using `kubectl`.

### 5. **Container Orchestration Services**
- Understood container orchestration as the automation of deploying, managing, scaling, and networking containers.
- Compared ECS and EKS as AWS's primary orchestration services.
- Learned about orchestration benefits: scalability, high availability, and load balancing.

### 6. **Amazon ECR (Elastic Container Registry)**
- Explored Amazon ECR, a fully managed Docker container registry for storing, managing, and deploying container images.
- Learned how to push and pull container images to/from ECR using the AWS CLI or Docker CLI.
- Understood ECR repository policies and integration with ECS and EKS.

### 7. **Where Containers Run: EC2 or Fargate?**
- Studied the two primary compute options for running containers in AWS:
  - **Amazon EC2**: Provides virtual servers where you manage the underlying infrastructure (e.g., scaling, patching).
  - **AWS Fargate**: A serverless compute engine for containers, eliminating the need to manage servers.
- Compared use cases: EC2 for more control over infrastructure, Fargate for simplified management and auto-scaling.
- Learned that ECS and EKS support both EC2 and Fargate as launch types.

### 8. **How to Run Containers**
- Explored the process of running containers in AWS:
  1. **Create a container image**: Build a Docker image locally or use an existing one.
  2. **Push to ECR**: Authenticate Docker with ECR and push the image to a repository.
  3. **Configure ECS/EKS**: Define a task (ECS) or pod (EKS) with the container image.
  4. **Choose compute**: Select EC2 or Fargate as the launch type.
  5. **Deploy and manage**: Use ECS services or EKS deployments to run and scale containers.
- Practiced deploying a sample containerized application on ECS with Fargate.

## Key Takeaways
- AWS Lambda is ideal for event-driven, serverless workloads.
- Containers provide portability and consistency across environments.
- ECS and EKS are powerful orchestration tools, with ECS being simpler and EKS offering Kubernetes flexibility.
- ECR simplifies container image management, and Fargate eliminates server management overhead.
- Choosing between EC2 and Fargate depends on the level of control and operational simplicity needed.

