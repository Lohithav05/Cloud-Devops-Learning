# Cloud-DevOps Learning Journey: Day 7 
*Date: July 16, 2025*

## Overview
Day 7 of the Cloud-DevOps learning journey focuses on directing traffic with **Elastic Load Balancing (ELB)**, understanding its benefits, exploring routing methods, and diving into messaging and queuing with **Amazon SQS** and **Amazon SNS**. These AWS services are critical for building scalable, resilient, and decoupled applications in the cloud.

## 1. Elastic Load Balancing (ELB)

### What is ELB?
Elastic Load Balancing automatically distributes incoming application or network traffic across multiple targets, such as Amazon EC2 instances, containers, IP addresses, or Lambda functions, in one or more Availability Zones (AZs). ELB ensures high availability, fault tolerance, and scalability by routing traffic only to healthy targets.[](https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/what-is-load-balancing.html)[](https://aws.amazon.com/elasticloadbalancing/)

### Benefits of ELB
- **High Availability**: Distributes traffic across multiple AZs, ensuring the application remains available even if one AZ fails.[](https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/how-elastic-load-balancing-works.html)
- **Automatic Scaling**: Scales load balancer capacity automatically based on traffic demand, handling spikes without manual intervention.[](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/introduction.html)

### Routing Methods
ELB uses listeners and rules to direct traffic to target groups. Key routing methods include:
- **Round Robin (Default)**: Distributes traffic evenly across all healthy targets in a target group.[](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/introduction.html)
- **Least Outstanding Requests**: Routes traffic to the target with the fewest active requests, optimizing for uneven workloads.[](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/introduction.html)
- **Path-Based Routing (ALB)**: Routes traffic based on URL paths (e.g., `/api` to one target group, `/web` to another).[](https://medium.com/%40christopheradamson253/advanced-load-balancing-techniques-with-aws-elb-bf4aff32dcc6)[](https://aws.amazon.com/blogs/containers/using-aws-application-load-balancer-path-based-routing-to-combine-amazon-ecs-launch-types/)
- **Host-Based Routing (ALB)**: Routes traffic based on the host header, enabling multiple applications on a single load balancer.[](https://medium.com/%40Raghvendra_Tyagi/aws-elastic-load-balancer-overview-and-types-with-practical-c214cbdfdd9b)
- **Cross-Zone Load Balancing**: Distributes traffic across all enabled AZs, ensuring even distribution even if targets are unevenly spread across AZs. Enabled by default for ALB; optional for NLB.[](https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/how-elastic-load-balancing-works.html)[](http://www.ebsguide.com/81-elb/)
- **Flow Hash (NLB)**: Routes each TCP connection to a single target for the connection's duration, based on protocol, source/destination IP, and port.[](https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/how-elastic-load-balancing-works.html)

## 2. Messaging and Queuing

### Amazon Simple Queue Service (SQS)
Amazon SQS is a fully managed message queuing service that enables decoupling and asynchronous communication between application components.[](https://github.com/kananinirav/AWS-Certified-Cloud-Practitioner-Notes/blob/master/practice-exam/practice-exam-2.md)

#### Key Features
- **Queue Types**:
  - **Standard Queues**: High throughput, at-least-once delivery, best-effort ordering.
  - **FIFO Queues**: Guaranteed message order and exactly-once delivery for applications requiring strict sequencing.
- **Scalability**: Handles millions of messages with automatic scaling.
- **Reliability**: Stores messages redundantly across multiple AZs.
- **Use Cases**: Decoupling microservices, buffering tasks, and processing asynchronous workflows (e.g., image resizing, ETL jobs).[](https://blog.besharp.it/3-ways-to-decouple-your-microservices-sqs-queues-elb-load-balancing-and-sns-notification-system/)

#### How SQS Works
- Producers send messages to an SQS queue.
- Consumers (e.g., EC2 instances, Lambda functions) poll the queue to retrieve messages.
- Messages are processed and deleted from the queue to prevent reprocessing (unless configured otherwise).
- Supports visibility timeouts to prevent multiple consumers from processing the same message simultaneously.[](https://blog.besharp.it/3-ways-to-decouple-your-microservices-sqs-queues-elb-load-balancing-and-sns-notification-system/)

### Amazon Simple Notification Service (SNS)
Amazon SNS is a fully managed pub/sub messaging service that enables event-driven communication by sending messages to multiple subscribers.[](https://aws.amazon.com/blogs/compute/event-driven-computing-with-amazon-sns-compute-storage-database-and-networking-services/)

#### Key Features
- **Topics**: Logical channels for publishing messages.
- **Subscribers**: Can include SQS queues, Lambda functions, HTTP endpoints, email, SMS, or mobile push notifications.
- **Fanout Architecture**: Sends a single message to multiple subscribers for parallel processing.
- **Reliability**: Delivers messages to multiple AZs for high availability.
- **Use Cases**: Triggering notifications, coordinating microservices, and automating workflows (e.g., sending alerts for failed ETL jobs or low storage).[](https://aws.amazon.com/blogs/compute/event-driven-computing-with-amazon-sns-compute-storage-database-and-networking-services/)

#### How SNS Works
- Publishers send messages to an SNS topic.
- SNS fans out messages to all subscribed endpoints (e.g., SQS queues, Lambda functions).
- Subscribers process messages independently, enabling decoupling and scalability.[](https://aws.amazon.com/blogs/compute/event-driven-computing-with-amazon-sns-compute-storage-database-and-networking-services/)

## Practical Example
Consider an e-commerce application:
- **ELB**: An ALB routes HTTP traffic to EC2 instances running the web frontend (`/web`) and API backend (`/api`) using path-based routing. It ensures high availability across multiple AZs and scales with traffic spikes during sales events.[](https://medium.com/%40christopheradamson253/advanced-load-balancing-techniques-with-aws-elb-bf4aff32dcc6)
- **SQS**: Handles asynchronous order processing by queuing orders from the API backend, allowing worker nodes to process payments and inventory updates without overwhelming the system.[](https://blog.besharp.it/3-ways-to-decouple-your-microservices-sqs-queues-elb-load-balancing-and-sns-notification-system/)
- **SNS**: Notifies multiple services (e.g., inventory, shipping) via a topic when an order is placed, ensuring real-time updates across microservices.[](https://aws.amazon.com/blogs/compute/event-driven-computing-with-amazon-sns-compute-storage-database-and-networking-services/)

