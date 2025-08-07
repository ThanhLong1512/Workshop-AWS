---
title: "Xây dựng Ứng dụng Containerized trên AWS với CI/CD Pipeline"
date: "2025-06-21"
weight: 1
chapter: false
---

# Xây dựng Ứng dụng Containerized trên AWS với CI/CD Pipeline

### Tổng quan

Workshop này hướng dẫn bạn xây dựng một hệ thống ứng dụng web containerized hoàn chỉnh trên AWS với CI/CD pipeline tự động. Chúng ta sẽ bắt đầu từ việc phát triển ứng dụng trên GitHub, thiết lập Docker containers, triển khai lên AWS thông qua load balancer, và tích hợp các dịch vụ bảo mật, monitoring, và notification.

### Kiến trúc bao gồm

- Frontend: React.js application containerized
- Backend: Node.js/Express.js API containerized
- Database: MongoDB hoặc PostgreSQL
- Security: KMS encryption, SNS notifications
- Monitoring: CloudWatch metrics và alerts

![ConnectPrivate](/images/WorkShop_Architecture.png)

### Mục đích

- Học Container Technology: Hiểu rõ Docker containerization, cách đóng gói và triển khai ứng dụng.
- Xây dựng CI/CD Pipeline: Tự động hóa quy trình build, test, deploy từ GitHub đến AWS.
- Quản lý Infrastructure: Thiết lập load balancing, auto scaling, security groups và networking.
- Bảo mật và Monitoring: Tích hợp WAF, KMS encryption, CloudWatch monitoring và SNS alerts.
- Production Ready: Xây dựng hệ thống highly available, scalable và secure cho môi trường production.

### Chi phí ước tính

- AWS Free Tier: EC2 t2.micro, ALB (750 hours/tháng)
- CloudFront: $0.085/GB cho 10TB đầu tiên
- Route 53: $0.50/hosted zone/tháng
- KMS: $1/key/tháng + $0.03/10,000 requests
- SNS: $0.50/1 million requests
- Ước tính tổng: $10-30/tháng tùy theo traffic

### Nội dung

1.  [Giới thiệu](1-introduce/)
2.  [Các bước chuẩn bị](2-Prerequiste/)
3.  [Thiết lập và Containerization](3-Containerization/)
4.  [Bảo mật và giám sát phần mềm](4-Security&Monitoring/)
5.  [Dọn dẹp tài nguyên](5-cleanup/)
