---
title: "Monitor and automatically notify with CloudWatch and SNS"
date: "2025-06-21"
weight: 3
chapter: false
pre: " <b> 4.3 </b> "
---

## Introduction

In today's cloud environments, continuous monitoring and rapid incident response are critical factors determining application success. Amazon CloudWatch and Amazon Simple Notification Service (SNS) form a powerful monitoring and alerting system that enables 24/7 application performance tracking and instant notifications when anomalies occur.

**Amazon CloudWatch - The Eyes of AWS Infrastructure**

- **Amazon CloudWatch** is a comprehensive monitoring and observability service that provides visibility into all your AWS resources and applicationsạn

**Amazon SNS - Multi-Channel Notification System**

- **Amazon Simple Notification Service (SNS)** is a fully managed messaging service that enables notifications to multiple endpoints

With CloudWatch and SNS, you can build an intelligent monitoring system that automatically detects anomalies and ensures operations teams are promptly informed about system status. This forms the foundation for effective DevOps practices and reliable system operations.

## Implementation Steps

**Step 1:** Navigate to **AWS Console -> CloudWatch**
![Visual Studio Code](/images/4.Security&Monitoring/4.3/1.png)
**Step 2:** Select **Logs -> Log groups -> Create log group**
![Visual Studio Code](/images/4.Security&Monitoring/4.3/2.png)
**Step 3:** Configure the following settings:

- Log group name: **Mernstack-Cloudwatch**
- Retention setting: **1 days**
- Log class: **Standard**

**Step 4:** Select **Create**
![Visual Studio Code](/images/4.Security&Monitoring/4.3/3.png)
**Step 5:** After successfully creating the Log group, navigate to **AWS Console -> WAF & Shield**

**Step 6:** Select **Mernstack-WAF ->Logging and metrics**
![Visual Studio Code](/images/4.Security&Monitoring/4.3/4.png)
**Step 7:** Select **Enable-> Logging destination**
![Visual Studio Code](/images/4.Security&Monitoring/4.3/5.png)
**Step 8:** Select the Log Group you created, Redacted fields: **HTTP Method**, then select **Save**

**Step 9:** Navigate to **AWS Console -> Simple Notification Service -> Next step**
![Visual Studio Code](/images/4.Security&Monitoring/4.3/6.png)
**Step 10:** Configure the following settings:

- Type: **Standard**
- Name: **Mernstack-SNS**

**Advanced options:**

- Delivery retry policy: **Default**
- Delivery status logging: **Disabled (for lab)**
- Encryption: **Disabled (for lab)**
- Access policy: **Default**
  ![Visual Studio Code](/images/4.Security&Monitoring/4.3/7.png)

**Step 11:** Select **Create Topic** and then verify the result
![Visual Studio Code](/images/4.Security&Monitoring/4.3/8.png)
**Step 12:** Select **Create subscription**
![Visual Studio Code](/images/4.Security&Monitoring/4.3/9.png)
**Step 13:** Select Protocol: **Email**, Endpoint: **nguyenboo2018@gmail.com**
![Visual Studio Code](/images/4.Security&Monitoring/4.3/10.png)
**Step 14:** Select **Create Subscription**
![Visual Studio Code](/images/4.Security&Monitoring/4.3/11.png)
![Visual Studio Code](/images/4.Security&Monitoring/4.3/12.png)
**Step 15:** Navigate to **AWS CloudWatch -> Alarm -> In Alarm -> Create alarm**
![Visual Studio Code](/images/4.Security&Monitoring/4.3/13.png)
**Step 16:** Configure the following:

- Select **select metric -> EC2 -> Mernstack-EC2**
  ![Visual Studio Code](/images/4.Security&Monitoring/4.3/14.png)
- Configure as shown below
  ![Visual Studio Code](/images/4.Security&Monitoring/4.3/15.png)
  ![Visual Studio Code](/images/4.Security&Monitoring/4.3/16.png)
- Set Alarm Name: **Mernstack-Alarm then select Next -> Create Alarm**
  ![Visual Studio Code](/images/4.Security&Monitoring/4.3/17.png)
