---
title: "Building a Containerized Web Application on AWS with CI/CD Pipeline"
date: "2025-06-21"
weight: 1
chapter: false
---

# Building a Containerized Web Application on AWS with CI/CD Pipeline

### Overview

This workshop guides you through building a complete containerized web application system on AWS with an automated CI/CD pipeline. Starting from application development on GitHub, we’ll cover Docker containerization, deployment to AWS via load balancers, and integration of security, monitoring, and notification services.

### Architecture Includes

- Frontend: React.js (containerized)

- Backend: Node.js/Express.js API (containerized)

- Database: MongoDB or PostgreSQL

- Security: KMS encryption, SNS notifications

- Monitoring: CloudWatch metrics and alerts

![ConnectPrivate](/images/arc-workshop.png)

### Objectives

- Learn Container Technology: Master Docker containerization for packaging and deploying applications.

- Build CI/CD Pipeline: Automate build, test, and deploy workflows from GitHub to AWS.

- Infrastructure Management: Configure load balancing, auto-scaling, security groups, and networking.

- Security & Monitoring: Integrate WAF, KMS encryption, CloudWatch, and SNS alerts.

- Production-Ready: Deploy a highly available, scalable, and secure system.

### Estimated Costs

- AWS Free Tier: EC2 t2.micro, ALB (750 hours/month)

- CloudFront: $0.085/GB for the first 10TB

- Route 53: $0.50/hosted zone/month

- KMS: $1/key/month + $0.03/10,000 requests

- SNS: $0.50/1 million requests

- Total Estimate: $10–30/month (varies by traffic)

### Workshop Steps

1.  [Introduction](1-introduce/)
2.  [Prerequisites](2-Prerequiste/)
3.  [Application Containerization](3-Containerization/)
4.  [Security & Monitoring](4-Security&Monitoring/)
5.  [Cleanup Resource](5-cleanup/)
