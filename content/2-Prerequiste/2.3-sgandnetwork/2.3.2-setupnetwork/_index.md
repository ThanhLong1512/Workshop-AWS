---
title: "Setup Network"
date: "2025-06-21"
weight: 2
chapter: false
pre: " <b> 2.3.2 </b> "
---

### Creating NAT Gateway

**Overview**

- NAT Gateway allows instances in private subnets to connect to the internet
- Ensures one-way connectivity from inside to outside, enhancing security
- Requires Elastic IP and must be placed in a public subnet

### NAT Gateway Deployment

1. Access VPC Dashboard
   - Select **NAT Gateways**
   - Choose **Create NAT gateway**

![Gateway](/images/2.prerequisite/2.3/2.3.2/8.png)

2. Configure **NAT Gateway**

- **Name**: Enter **mernstack-gateway-public**
- **Subnet**: Select **Mern-stack Subnet**
- **Connectivity type**: Select **Public**
- **Elastic IP allocation ID**: Select Elastic IP vừa tạo

![Gateway](/images/2.prerequisite/2.3/2.3.2/7.png)

3. Select **Create NAT gateway**

![Gateway](/images/2.prerequisite/2.3/2.3.2/9.png)

4. Confirm successful **NAT Gateway** creation

### Creating Internet Gateway

**Overview**

- Internet Gateway (IGW) is a VPC component that enables internet connectivity
- Provides connection point between VPC and the internet
- Supports bidirectional communication for resources within VPC

#### Internet Gateway Deployment

1. Access **VPC** Dashboard
   - Select **Internet Gateways** from the left menu
   - Click **Create internet gateway**

![Gateway](/images/2.prerequisite/2.3/2.3.2/13.png)

2. Configure **Internet Gateway**
   - In Name tag, enter **mernstack-igw**
   - Click Create internet gateway

![Gateway](/images/2.prerequisite/2.3/2.3.2/14.png)

3. Confirm successful Internet Gateway creation

![Gateway](/images/2.prerequisite/2.3/2.3.2/15.png)

**VPC Connection**

4.  Attach Internet Gateway to VPC
    - Click **Actions**
    - Select **Attach to VPC**
    - Select **Mern-stack VPC** từ danh sách (VPC ID sẽ tự động điền)
    - Click **Attach internet gateway**

![Gateway](/images/2.prerequisite/2.3/2.3.2/17.png)
![Gateway](/images/2.prerequisite/2.3/2.3.2/18.png)

5.  After successful attachment:

![Gateway](/images/2.prerequisite/2.3/2.3.2/16.png)

### Creating Route Table

**Overview**

- Route Table is a component that routes network traffic within VPC
- Determines the path for packets between subnets and the internet
- Allows control of data flow in/out of VPC

#### Route Table Deployment

1. Access **VPC** Dashboard

   - Select **Route Tables** from the left menu
   - Click **Create route table**

2. Configure **Route Table**
   - **Name**: Enter **mernstack-route-tables**
   - **VPC**: Select **Mern-stack VPC**
   - Select **Create route table**

![Gateway](/images/2.prerequisite/2.3/2.3.2/10.png)

3. Confirm successful **Route Table** creation

![Gateway](/images/2.prerequisite/2.3/2.3.2/11.png)

**Routing Configuration**

4. Add route for **Internet Gateway**
   - Select **Actions**
   - Select **Edit routes**

![Gateway](/images/2.prerequisite/2.3/2.3.2/12.png)

5. Configure new route
   - Click **Add route**
   - **Destination**: Enter 0.0.0.0/0 (represents the internet)
   - **Target**: Select **mernstack-igw** and choose the created IGW
   - **Target**: Select **mernstack-gateway-public** and choose the created NAT Gateway
   - Click **Save changes**

![Gateway](/images/2.prerequisite/2.3/2.3.2/23.png)

**Subnet Association**

6. Set up subnet associations
   - Select **Subnet associations** tab
   - Click **Edit subnet associations**

![Gateway](/images/2.prerequisite/2.3/2.3.2/20.png)

7. Select subnets
   - Choose Subnet: **Mern-stack Subnet**
   - Click **Save associations**

![Gateway](/images/2.prerequisite/2.3/2.3.2/21.png)

8. Confirm successful subnet associations configuration

![Gateway](/images/2.prerequisite/2.3/2.3.2/22.png)
