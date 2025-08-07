---
title: "Bảo vệ ứng dụng web với AWS WAF"
date: "2025-06-21"
weight: 2
chapter: false
pre: " <b> 4.2 </b> "
---

## Giới thiệu

AWS WAF (Web Application Firewall) là một dịch vụ bảo mật đám mây mạnh mẽ được thiết kế để bảo vệ ứng dụng web của bạn khỏi các cuộc tấn công mạng phổ biến và lưu lượng truy cập độc hại. Hoạt động tại tầng ứng dụng (Layer 7 của mô hình OSI), AWS WAF cung cấp khả năng kiểm soát chi tiết đối với lưu lượng HTTP/HTTPS đến ứng dụng của bạn.

## Tại sao cần AWS WAF?

Trong bối cảnh an ninh mạng ngày càng phức tạp, các ứng dụng web phải đối mặt với nhiều loại tấn công khác nhau:

- SQL Injection: Kẻ tấn công chèn mã SQL độc hại vào các truy vấn database
- Cross-Site Scripting (XSS): Tiêm mã JavaScript độc hại vào trang web
- DDoS Attack: Làm quá tải server bằng lượng request khổng lồ
- Bot Traffic: Các bot độc hại có thể scrape dữ liệu hoặc tạo fake traffic
- Geographic Attacks: Tấn công từ các vùng địa lý nguy hiểm

AWS WAF hoạt động như một lá chắn bảo vệ, lọc và kiểm soát mọi request trước khi chúng đến được ứng dụng của bạn.

## Các bước thực hiện

**Bước 1:** Truy cập **AWS Console -> EC2 -> Target groups-> Create target group**
![Visual Studio Code](/images/4.Security&Monitoring/4.2/2.png)
**Bước 2:** Thực hiện cấu hình bên dưới:

- Target group name: **Mernstack-TG**
- VPC: **Mernstack-VPC**
- Register target: **Mernstack-EC2**

**Bước 3:** Sau khi đã cấu hình trên thì chọn **Create target group**
![Visual Studio Code](/images/4.Security&Monitoring/4.2/3.png)

**Bước 4:** Truy cập **AWS Console -> EC2 -> Load Balancer -> Create load balancer**
![Visual Studio Code](/images/4.Security&Monitoring/4.2/1.png)
**Bước 5:** Thực hiện các cấu hình bên dưới:

- Load balancer name: **Mernstack-ALB**
- Scheme: **Internet-facing**
- IP address type: **IPv4**
- VPC: **Mern-stack VPC**
- Availability Zones: **Mern-stack Subnet** và **Mern-stack Subnet 02**
- Security group: **alb-security-group**
- Default Action: **Mernstack-TG**
- Optimize with service integration:**WAF**

**Bước 6:** Sau khi đã cấu hình xong thì chọn **Create load balancer**
![Visual Studio Code](/images/4.Security&Monitoring/4.2/4.png)
**Bước 7:** Truy cập **AWS Console -> WAF & Shield**
![Visual Studio Code](/images/4.Security&Monitoring/4.2/5.png)
**Bước 8:** Chọn **Create web ACL**
**Bước 9:** Thực hiện cấu hình bên dưới:

- Region: **Asia Pacific (Singapore)**
- Name: **Mernstack-WAF**
- Resources: Chọn **Application -> Mernstack-ALB**
  ![Visual Studio Code](/images/4.Security&Monitoring/4.2/6.png)
- Rule: Chọn **Add Rule -> Add managed rule groups**
  ![Visual Studio Code](/images/4.Security&Monitoring/4.2/7.png)
  **Bước 10** Tiến hành tạo **Create web ACL**
  ![Visual Studio Code](/images/4.Security&Monitoring/4.2/8.png)
