---
title: "Introduction"
date: "2025-06-21"
weight: 1
chapter: false
pre: " <b> 1. </b> "
---

### Overview

This architecture describes a Serverless Web Application built entirely on AWS, leveraging managed services to create a highly scalable, cost-optimized, and secure application. The application follows a 3-tier architecture model, consisting of frontend, backend, and supporting services.

### Key Components of the Architecture

1. **User Access & Code Management**
   - GitHub: Source code management and version control for the entire application
   - User: End-users accessing the application via web browsers
2. **Security & Network Layer (Lớp bảo mật và mạng)**
   ![ConnectPrivate](/images/aws_route53.png)
   **AWS Route 53** is a highly scalable and reliable DNS (Domain Name System) service. It routes user requests to AWS infrastructure, such as EC2 instances, Elastic Load Balancers, or Amazon S3 buckets. Route 53 can also direct traffic to non-AWS infrastructure.
   ![ConnectPrivate](/images/aws_alb.png)
   **AWS Application Load Balancer (ALB)** operates at Layer 7 (Application Layer) of the OSI model, routing traffic based on request content. ALB supports path-based and host-based routing, distributing traffic across multiple target groups. It integrates seamlessly with AWS services like Auto Scaling, ECS, and Lambda.
   ![ConnectPrivate](/images/aws_cloudfront.png)
   **AWS CloudFront** is a global Content Delivery Network (CDN) that delivers content with low latency and high transfer speeds. It caches content at edge locations worldwide, reducing page load times and improving user experience.
   ![ConnectPrivate](/images/aws_waf.png)
   **AWS WAF (Web Application Firewall)** protects applications from common web exploits like SQL injection and cross-site scripting (XSS). It allows custom rules to filter, monitor, and block malicious traffic based on IP addresses, HTTP headers, HTTP body, or URI strings.
3. **Application Layer (Lớp ứng dụng)**
   - **Frontend Container**
     - Runs on port 80
     - Uses Nginx as the web server
     - Can host React, Angular, or Vue.js applications
     - Port 4375 for internal communications
   - **Backend Container**
     - Runs on port 4000
     - Uses Express.js (Node.js) framework
     - Handles business logic & API endpoints
     - Connects with other AWS services
4. **AWS Managed Services**
   ![ConnectPrivate](/images/aws_ec2.png)
   **Amazon EC2 (Elastic Compute Cloud)** provides scalable compute capacity in the cloud. Users can launch virtual servers (instances) with customizable CPU, memory, storage, and networking configurations. EC2 offers various instance types optimized for different workloads (compute-optimized, memory-optimized, storage-optimized).
   ![ConnectPrivate](/images/aws_kms.png)
   **AWS KMS (Key Management Service)** is a fully managed encryption key service for creating and controlling cryptographic keys. It integrates with most AWS services to protect stored data and uses Hardware Security Modules (HSMs) for enhanced security.
   ![ConnectPrivate](/images/aws_cloudwatch.png)
   **Amazon CloudWatch** is a monitoring and observability service for DevOps engineers, developers, SREs, and IT managers. It provides actionable insights to monitor applications, track system-wide performance changes, optimize resource usage, and maintain operational health..
   ![ConnectPrivate](/images/aws_s3.png)
   **Amazon S3 (Simple Storage Service)** is a highly durable object storage service for storing and retrieving any amount of data. It offers 99.999999999% (11 nines) durability and powers millions of applications worldwide. S3 includes management features for data organization and fine-grained access control.
   ![ConnectPrivate](/images/aws_sns.png)
   **Amazon SNS (Simple Notification Service)** is a fully managed messaging service for application-to-application (A2A) and application-to-person (A2P) communication. It enables high-throughput, push-based, many-to-many messaging for distributed systems, microservices, and serverless applications.
5. **Database & Data Processing**
   - **MongoDB**: NoSQL database for application data storage
   - Integrated with the **AWS ecosystem** via managed services
