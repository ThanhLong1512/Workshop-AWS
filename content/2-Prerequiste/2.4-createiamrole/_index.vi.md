---
title: "Tạo IAM Role"
date: "2025-06-21"
weight: 4
chapter: false
pre: " <b> 2.4 </b> "
---

### Tạo IAM Role

Trong bước này chúng ta sẽ tiến hành tạo IAM Role. Trong IAM Role này sẽ được gán policy **WebsiteKMSPolicy**, đây là policy cho phép máy chủ EC2 có thể giao tiếp với Key Management Service.

1. Truy cập vào [giao diện quản trị dịch vụ IAM](https://console.aws.amazon.com/iamv2/)
2. Ở thanh điều hướng bên trái, click **Roles -> Create role**.

![role](/images/2.prerequisite/2.4/1.png)

3. Click **AWS service** và click **EC2**.

- Click **Next**.

![role](/images/2.prerequisite/2.4/2.png)

4. Trong ô Search, điền **WebsiteKMSPolicy** và ấn phím Enter để tìm kiếm policy này.

- Click chọn policy **WebsiteKMSPolicy**.
- Click **Next: Tags.**

![role](/images/2.prerequisite/2.4/3.png)

5. Click **Next: Review**.
6. Đặt tên cho Role là **Roles_ec2** ở Role Name

- Click **Create Role** \.

![role](/images/2.prerequisite/2.4/4.png)

7. Kiểm tra kết quả như hình bên dưới

![role](/images/2.prerequisite/2.4/5.png)
