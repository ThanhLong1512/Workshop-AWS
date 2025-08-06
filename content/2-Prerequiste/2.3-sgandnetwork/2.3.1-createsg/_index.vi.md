---
title: "Tạo Security Groups"
date: "2025-06-21"
weight: 1
chapter: false
pre: " <b> 2.3.1 </b> "
---

### Tạo Security Group trong Amazon VPC

**Tổng quan**

- Security Group là tường lửa ảo cho các tài nguyên AWS
- Hoạt động như danh sách kiểm soát truy cập (ACL) ở cấp instance
- Cho phép kiểm soát lưu lượng vào/ra theo port và protocol

**Tạo ALB Security Group**

1. Truy cập giao diện **VPC**

   - Chọn **Security Groups** từ menu bên trái
   - Click **Create security group**

![EC2](/images/2.prerequisite/2.3/2.3.1/1.png)

2. Cấu hình thông tin cơ bản

- **Security Group name**: Nhập **alb-security-group**
- **Description**: Security group for Application Load Balancer
- **VPC**: Chọn **Mern-stack VPC**
  ![EC2](/images/2.prerequisite/2.3/2.3.1/2.png)

3. Thiết lập Inbound Rule, Outbound Rule
   - Click Add rule
   - Rule 1:
     - **Type**: HTTP
     - **Source**: Anywhere (cho phép ping từ mọi nơi)
   - Rule 2:
     - **Type**: HTTPs
     - **Source**: Anywhere (cho phép ping từ mọi nơi)

![EC2](/images/2.prerequisite/2.3/2.3.1/3.png)

4. Xác nhận Inbound/Outbound Rules và tạo Security Group
5. Kiểm tra Security Group đã tạo
   ![EC2](/images/2.prerequisite/2.3/2.3.1/4.png)

**Tạo Application Security Group**

1. Truy cập giao diện **VPC**

   - Chọn **Security Groups** từ menu bên trái
   - Click **Create security group**

![EC2](/images/2.prerequisite/2.3/2.3.1/1.png)

2. Cấu hình thông tin cơ bản

- **Security Group name**: Nhập **app-security-group**
- **Description**: Security group for application containers
- **VPC**: Chọn **Mern-stack VPC**
  ![EC2](/images/2.prerequisite/2.3/2.3.1/5.png)

3. Thiết lập Inbound Rule, Outbound Rule

   - Click Add rule
   - Rule 1:
     - **Type**: HTTP
     - **Source**: Anywhere (cho phép ping từ mọi nơi)
   - Rule 2:
     - **Type**: HTTPs
     - **Source**: Anywhere (cho phép ping từ mọi nơi)

4. Xác nhận Inbound/Outbound Rules và tạo Security Group
5. Kiểm tra Security Group đã tạo
   ![EC2](/images/2.prerequisite/2.3/2.3.1/6.png)
