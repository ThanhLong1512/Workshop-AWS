---
title: "Creating Security Groups"
date: "2025-06-21"
weight: 2
chapter: false
pre: " <b> 2.3.1 </b> "
---

### Creating Security Groups in Amazon VPC

**Overview**

- Security Groups act as virtual firewalls for AWS resources
- Function as instance-level access control lists (ACLs)
- Enable control of inbound/outbound traffic by port and protocol

**Creating ALB Security Group**

1. Navigate to the **VPC** console

   - Select **Security Groups** from the left menu
   - Click **Create security group**

![EC2](/images/2.prerequisite/2.3/2.3.1/1.png)

2. Configure basic information

- **Security Group name**: Enter **alb-security-group**
- **Description**: Security group for Application Load Balancer
- **VPC**: Select **Mern-stack VPC**
  ![EC2](/images/2.prerequisite/2.3/2.3.1/2.png)

3. Set up Inbound/Outbound Rules
   - Click Add rule
   - Rule 1:
     - **Type**: HTTP
     - **Source**: Anywhere (allow ping from all locations)
   - Rule 2:
     - **Type**: HTTPs
     - **Source**: Anywhere (allow ping from all locations)

![EC2](/images/2.prerequisite/2.3/2.3.1/3.png)

4. Confirm Inbound/Outbound Rules and create the Security Group
5. Verify the created Security Group
   ![EC2](/images/2.prerequisite/2.3/2.3.1/4.png)

**Creating Application Security Group**

1. Navigate to the **VPC** console

   - Select **Security Groups** from the left menu
   - Click **Create security group**

![EC2](/images/2.prerequisite/2.3/2.3.1/1.png)

2. Configure basic information

- **Security Group name**: Enter **app-security-group**
- **Description**: Security group for application containers
- **VPC**: Select **Mern-stack VPC**
  ![EC2](/images/2.prerequisite/2.3/2.3.1/5.png)

3. Set up Inbound/Outbound Rules

   - Click Add rule
   - Rule 1:
     - **Type**: HTTP
     - **Source**: Anywhere (allow ping from all locations)
   - Rule 2:
     - **Type**: HTTPs
     - **Source**: Anywhere (allow ping from all locations)

4. Confirm Inbound/Outbound Rules and create the Security Group
5. Verify the created Security Group
   ![EC2](/images/2.prerequisite/2.3/2.3.1/6.png)
