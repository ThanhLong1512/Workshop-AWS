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

![Gateway](/images/2.prerequisite/2.3/2.3.2/8.png)

2. Cấu hình **NAT Gateway**

- **Name**: Nhập **mernstack-gateway-public**
- **Subnet**: Chọn **Mern-stack Subnet**
- **Connectivity type**: Chọn **Public**
- **Elastic IP allocation ID**: Chọn Elastic IP vừa tạo

![Gateway](/images/2.prerequisite/2.3/2.3.2/7.png)

3. Chọn **Create NAT gateway**

![Gateway](/images/2.prerequisite/2.3/2.3.2/9.png)

4. Xác nhận tạo thành công **NAT Gateway**

### Tạo Internet Gateway

**Tổng quan**

- Internet Gateway (IGW) là thành phần VPC cho phép kết nối internet
- Cung cấp điểm kết nối giữa VPC và internet
- Hỗ trợ giao tiếp hai chiều cho các tài nguyên trong VPC

#### Triển khai Internet Gateway

1. Truy cập giao diện VPC
   - Chọn **Internet Gateways** từ menu bên trái
   - Click vào **Create internet gateway**

![Gateway](/images/2.prerequisite/2.3/2.3.2/13.png)

2. Cấu hình Internet Gateway
   - Tại Name tag, nhập **mernstack-igw**
   - Click Create internet gateway

![Gateway](/images/2.prerequisite/2.3/2.3.2/14.png)

3. Xác nhận tạo Internet Gateway thành công

![Gateway](/images/2.prerequisite/2.3/2.3.2/15.png)

**Kết nối với VPC**

4.  Gắn Internet Gateway vào VPC
    - Click **Actions**
    - Chọn **Attach to VPC**
    - Chọn **Mern-stack VPC** từ danh sách (VPC ID sẽ tự động điền)
    - Click **Attach internet gateway**

![Gateway](/images/2.prerequisite/2.3/2.3.2/17.png)
![Gateway](/images/2.prerequisite/2.3/2.3.2/18.png)

5.  Sau khi gắn thành công:

![Gateway](/images/2.prerequisite/2.3/2.3.2/16.png)

### Tạo Route Table

**Tổng quan**

- Route Table là thành phần định tuyến lưu lượng mạng trong VPC
- Xác định đường đi cho các gói tin giữa các subnet và internet
- Cho phép kiểm soát luồng dữ liệu vào/ra VPC

#### Triển khai Route Table

1. Truy cập **VPC** Dashboard

   - Chọn **Route Tables** từ menu bên trái
   - Click vào **Create route table**

2. Cấu hình **Route Table**
   - **Name**: Nhập mernstack-route-tables
   - **VPC**: Chọn Mern-stack VPC
   - Chọn **Create route table**

![Gateway](/images/2.prerequisite/2.3/2.3.2/10.png)

3. Xác nhận tạo **Route Table** thành công

![Gateway](/images/2.prerequisite/2.3/2.3.2/11.png)

**Cấu hình định tuyến**

4. Thêm route cho Internet Gateway
   - Chọn **Actions**
   - Chọn **Edit routes**

![Gateway](/images/2.prerequisite/2.3/2.3.2/12.png)

5. Cấu hình route mới
   - Chọn **Add route**
   - **Destination**: Nhập 0.0.0.0/0 (đại diện cho internet)
   - **Target**: Chọn **mernstack-igw** và chọn IGW đã tạo
   - **Target**: Chọn **mernstack-gateway-public** và chọn NAT Gateway đã tạo
   - Click **Save changes**

![Gateway](/images/2.prerequisite/2.3/2.3.2/23.png)

**Liên kết với Subnet**

6. Thiết lập subnet associations
   - Chọn tab **Subnet associations**
   - Click **Edit subnet associations**

![Gateway](/images/2.prerequisite/2.3/2.3.2/20.png)

7. Chọn các subnet
   - Chọn Subnet: **Mern-stack Subnet**
   - Click **Save associations**

![Gateway](/images/2.prerequisite/2.3/2.3.2/21.png)

8. Xác nhận cấu hình subnet associations thành công

![Gateway](/images/2.prerequisite/2.3/2.3.2/22.png)
