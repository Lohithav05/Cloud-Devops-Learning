# AWS Cloud Practitioner – Module 1 Notes

## Cloud Computing Overview
Cloud computing is the on-demand delivery of IT resources over the internet with pay-as-you-go pricing. Users access computing services like servers, storage, databases, and software through a cloud provider’s infrastructure, eliminating the need to own physical servers or data centers.

## Service Models
### IaaS (Infrastructure as a Service) 🔧
- **Analogy**: You build the kitchen.
- Provides virtualized computing resources such as virtual machines, storage, and networking.
- Users manage operating systems, applications, and data, while the provider handles the underlying infrastructure (e.g., hardware, virtualization).
- Examples: Amazon EC2, Amazon S3.
- Use case: Hosting websites, running custom applications.
- Key benefit: Scalability and flexibility without physical hardware management.

### PaaS (Platform as a Service) 🎂
- **Analogy**: You get ingredients and an oven.
- Offers a platform for developing, running, and managing applications without managing infrastructure complexities (e.g., server maintenance, OS updates).
- Provider manages the runtime environment, middleware, and infrastructure.
- Examples: AWS Elastic Beanstalk, Google App Engine.
- Use case: Developing and deploying web applications quickly.
- Key benefit: Simplifies development by abstracting infrastructure management.

### SaaS (Software as a Service) 🍰
- **Analogy**: You buy a full cake.
- Delivers fully managed software applications over the internet, accessible via a subscription model.
- Users don’t manage the underlying infrastructure, platform, or application updates.
- Examples: Amazon WorkSpaces, Google Workspace, Salesforce.
- Use case: Email services, customer relationship management (CRM).
- Key benefit: Ease of use, as software is ready to use with minimal setup.

### FaaS (Function as a Service) 🍥
- **Analogy**: You order a slice only when you're hungry.
- Provides a serverless computing model where users run specific functions or code in response to events without managing servers.
- Provider handles all infrastructure, scaling, and execution environment.
- Examples: AWS Lambda, Azure Functions.
- Use case: Event-driven tasks like processing file uploads or automating workflows.
- Key benefit: Pay only for the compute time used, with automatic scaling.

## Deployment Models
### Cloud 🌩️
- **Definition**: Everything runs on the internet using cloud provider servers (e.g., AWS, Azure, Google Cloud). You don’t manage any hardware.
- **Example**: Storing your photos on Google Drive, where Google manages the servers, and you just upload and access files.
- **Key Benefit**: Flexibility to migrate and scale; design and build new applications entirely within the cloud.

### On-Premises 🏢
- **Definition**: Resources are deployed on computers/servers in your own office or company building, and you manage everything.
- **Example**: A bank uses its own secure data center in its building to store customer data, without relying on the internet.
- **Key Point**: Uses virtualization/resource management tools but lacks cloud benefits like scalability and on-demand resources.

### Hybrid 🔄
- **Definition**: A mix of cloud and on-premises, with some data/services on local servers and others in the cloud.
- **Example**: A hospital keeps sensitive patient data on local servers but uses cloud services for appointment booking and email.
- **Key Benefit**: Ideal for legacy systems that must stay on-premises, enabling gradual cloud adoption and better control over sensitive data.

## Summary
- **IaaS 🔧, PaaS 🎂, SaaS 🍰, and FaaS 🍥** represent different levels of abstraction in cloud computing, from managing infrastructure to serverless functions.
- **Cloud 🌩️, On-Premises 🏢, and Hybrid 🔄** deployment models offer flexibility based on organizational needs, costs, and data sensitivity.