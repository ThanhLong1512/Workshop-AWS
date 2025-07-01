---
title: "Thiết lập mạng"
date: "2025-06-21"
weight: 2
chapter: false
pre: " <b> 2.3.2 </b> "
---

### Tạo NAT Gateway

**Tổng quan**

- NAT Gateway cho phép các instances trong private subnet kết nối ra internet
- Đảm bảo kết nối một chiều từ trong ra ngoài, tăng tính bảo mật
- Cần có Elastic IP và đặt NAT Gateway trong public subnet

### Triển khai NAT Gateway

1. Truy cập VPC Dashboard
   - Chọn **NAT Gateways**
   - Chọn **Create NAT gateway**

![EC2](/images/2.prerequisite/2.3/2.3.1/8.png)

2. Cấu hình NAT Gateway

- **Name**: Nhập **mernstack-gateway-public**
- **Subnet**: Chọn **Mern-stack Subnet**
- **Connectivity type**: Chọn **Public**
- **Elastic IP allocation ID**: Chọn Elastic IP vừa tạo
  ![EC2](/images/2.prerequisite/2.3/2.3.1/7.png)

3. Chọn Create NAT gateway
