---
title: "Protect web applications with AWS WAF"
date: "2025-06-21"
weight: 2
chapter: false
pre: " <b> 4.2 </b> "
---

## Introduction

AWS WAF (Web Application Firewall) is a powerful cloud security service designed to protect your web applications from common cyberattacks and malicious traffic. Operating at the application layer (Layer 7 of the OSI model), AWS WAF provides granular control over HTTP/HTTPS traffic to your application.

## Why Use AWS WAF?

In today's increasingly complex cybersecurity landscape, web applications face various types of attacks:

- SQL Injection: Attackers inject malicious SQL code into database queries

- Cross-Site Scripting (XSS): Injecting malicious JavaScript into web pages

- DDoS Attacks: Overwhelming servers with massive request volumes

- Bot Traffic: Malicious bots scraping data or generating fake traffic

- Geographic Attacks: Attacks originating from high-risk regions

AWS WAF acts as a protective shield, filtering and controlling every request before it reaches your application.

## Implementation Steps

**Step 1:** Navigate to **AWS Console -> EC2 -> Target groups-> Create target group**
![Visual Studio Code](/images/4.Security&Monitoring/4.2/2.png)
**Step 2:** Configure the following settings:

- Target group name: **Mernstack-TG**
- VPC: **Mernstack-VPC**
- Register target: **Mernstack-EC2**

**Step 3:** After completing the configuration, select **Create target group**
![Visual Studio Code](/images/4.Security&Monitoring/4.2/3.png)

**Step 4:** Navigate to **AWS Console -> EC2 -> Load Balancer -> Create load balancer**
![Visual Studio Code](/images/4.Security&Monitoring/4.2/1.png)
**Step 5:** Configure the following settings:

- Load balancer name: **Mernstack-ALB**
- Scheme: **Internet-facing**
- IP address type: **IPv4**
- VPC: **Mern-stack VPC**
- Availability Zones: **Mern-stack Subnet** và **Mern-stack Subnet 02**
- Security group: **alb-security-group**
- Default Action: **Mernstack-TG**
- Optimize with service integration:**WAF**

**Step 6:** After completing the configuration, select **Create load balancer**
![Visual Studio Code](/images/4.Security&Monitoring/4.2/4.png)
**Step 7:** Navigate to **AWS Console -> WAF & Shield**
![Visual Studio Code](/images/4.Security&Monitoring/4.2/5.png)
**Step 8:** Select **Create web ACL**
**Step 9:** Configure the following settings:

- Region: **Asia Pacific (Singapore)**
- Name: **Mernstack-WAF**
- Resources: Chọn **Application -> Mernstack-ALB**
  ![Visual Studio Code](/images/4.Security&Monitoring/4.2/6.png)
- Rule: Chọn **Add Rule -> Add managed rule groups**
  ![Visual Studio Code](/images/4.Security&Monitoring/4.2/7.png)
  **Step 10** Tiến hành tạo **Create web ACL**
  ![Visual Studio Code](/images/4.Security&Monitoring/4.2/8.png)
