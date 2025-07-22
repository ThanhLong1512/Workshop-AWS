---
title: "Tạo Linux EC2"
date: "2025-06-21"
weight: 5
chapter: false
pre: " <b> 2.1.3 </b> "
---

1. Truy cập [giao diện quản trị dịch vụ EC2](https://console.aws.amazon.com/ec2/v2/home)

- Click **Instances**.
- Click **Launch instances**.

![EC2](/images/2.prerequisite/027-createec2.png)

2. **Name**: Nhập **Mern-stack EC2**

3. Trong bước chọn AMI

   - Chọn **Quick Start**
   - Chọn **Ubuntu**
   - AMI: chọn **Ubuntu Server 24.04 LTS**

![EC2](/images/2.prerequisite/2.1/2.1.3/1.png)

4. Trong phần key pair

- Click chọn **Create key pair**.
- Chọn và điền thông tin như trên hình

![EC2](/images/2.prerequisite/2.3/2.png)

**Security Note**

- Key pair là thành phần quan trọng để xác thực khi kết nối đến EC2 instance. Lưu trữ file .pem ở nơi an toàn và không chia sẻ với người khác. Mất key pair có thể dẫn đến việc không thể truy cập vào instance của bạn.

5. Tiếp theo, chúng ta thực hiện cấu hình network cho instance

- Tại mục **Network** chọn **Mern-stack VPC**.
- Tại mục **Subnet** chọn **Mern-stack Subnet**.
- Tại mục **Auto-assign Public IP** chọn **Use subnet setting (Enable)**

![EC2](/images/2.prerequisite/2.3/3.png)

6. Kiểm tra lại và chọn Launch instance

7. Hoàn thành khởi tạo instance. Tiến hành xem chi tiết instance bằng cách chọn **View all instance**

![EC2](/images/2.prerequisite/2.3/4.png)

8. Đợi khoảng 5 phút sau khi khởi tạo, Status check chuyển sang 2/2 check passed và trạng thái instance là Running

**Pro Tip**: Status check “2/2 checks passed” xác nhận rằng cả kiểm tra hệ thống (do AWS thực hiện) và kiểm tra instance (do hệ điều hành thực hiện) đều thành công. Điều này đảm bảo instance của bạn đã sẵn sàng để sử dụng.
