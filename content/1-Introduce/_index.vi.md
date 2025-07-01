---
title: "Giới thiệu"
date: "2025-06-21"
weight: 1
chapter: false
pre: " <b> 1. </b> "
---

### Tổng quan

Kiến trúc này mô tả một **Serverless Web Application** được xây dựng hoàn toàn trên nền tảng AWS, sử dụng các dịch vụ managed để tạo ra một ứng dụng có khả năng mở rộng cao, chi phí tối ưu và bảo mật tốt. Ứng dụng được thiết kế theo mô hình 3-tier architecture với frontend, backend và các dịch vụ hỗ trợ.

### Các thành phần chính trong kiến trúc

1. **User Access & Code Management**
   - GitHub: Quản lý mã nguồn và version control cho toàn bộ ứng dụng
   - User: Người dùng cuối truy cập ứng dụng thông qua web browser
2. **Security & Network Layer (Lớp bảo mật và mạng)**
   ![ConnectPrivate](/images/aws_route53.png)
   **AWS Route 53** là dịch vụ DNS (Domain Name System) có khả năng mở rộng cao và độ tin cậy cao của AWS. Route 53 kết nối các yêu cầu của người dùng với cơ sở hạ tầng chạy trên AWS như EC2 instances, Elastic Load Balancers hoặc Amazon S3 buckets. Route 53 cũng có thể được sử dụng để định tuyến người dùng đến cơ sở hạ tầng bên ngoài AWS.
   ![ConnectPrivate](/images/aws_alb.png)
   **AWS Application Load Balancer (ALB)** hoạt động ở layer 7 của mô hình OSI (Application Layer) và có thể định tuyến traffic dựa trên nội dung của request. ALB hỗ trợ path-based routing và host-based routing, có thể phân phối traffic đến nhiều target groups khác nhau. ALB tích hợp tốt với các dịch vụ AWS khác như Auto Scaling, ECS, và Lambda
   ![ConnectPrivate](/images/aws_cloudfront.png)
   **AWS CloudFront** là dịch vụ Content Delivery Network (CDN) toàn cầu giúp phân phối nội dung với độ trễ thấp và tốc độ truyền tải cao. CloudFront sử dụng mạng lưới các edge locations trên toàn thế giới để cache nội dung gần người dùng cuối nhất, giảm thiểu thời gian load trang và cải thiện trải nghiệm người dùng.
   ![ConnectPrivate](/images/aws_waf.png)
   **AWS WAF (Web Application Firewall)** là dịch vụ firewall ứng dụng web giúp bảo vệ ứng dụng khỏi các cuộc tấn công web phổ biến như SQL injection, cross-site scripting (XSS). WAF cho phép tạo các rule tùy chỉnh để filter, monitor và block traffic độc hại dựa trên các điều kiện như IP addresses, HTTP headers, HTTP body, hoặc URI strings.
3. **Application Layer (Lớp ứng dụng)**
   - **Frontend Container**
     - Chạy trên port 80
     - Sử dụng Nginx làm web server
     - Có thể chứa ứng dụng React, Angular hoặc Vue.js
     - Port 4375 cho các kết nối nội bộ
   - **Backend Container**
     - Chạy trên port 4000
     - Sử dụng Express.js framework (Node.js)
     - Xử lý business logic và API endpoints
     - Kết nối với các dịch vụ AWS khác
4. **AWS Managed Services**
   ![ConnectPrivate](/images/aws_ec2.png)
   **Amazon EC2 (Elastic Compute Cloud)** cung cấp khả năng tính toán có thể mở rộng trong cloud. EC2 cho phép khởi chạy các máy chủ ảo (instances) với nhiều cấu hình khác nhau về CPU, memory, storage và network. Người dùng có thể chọn từ nhiều loại instance types được tối ưu hóa cho các workload khác nhau như compute-optimized, memory-optimized, storage-optimized.
   ![ConnectPrivate](/images/aws_kms.png)
   **AWS KMS (Key Management Service)** là dịch vụ quản lý khóa mã hóa được quản lý hoàn toàn, giúp tạo và kiểm soát các khóa mã hóa được sử dụng để mã hóa dữ liệu. KMS tích hợp với hầu hết các dịch vụ AWS khác để bảo vệ dữ liệu được lưu trữ trong các dịch vụ đó. KMS sử dụng Hardware Security Modules (HSMs) để bảo vệ tính bảo mật của khóa.
   ![ConnectPrivate](/images/aws_cloudwatch.png)
   **Amazon CloudWatch** là dịch vụ monitoring và observability được xây dựng cho DevOps engineers, developers, site reliability engineers (SREs) và IT managers. CloudWatch cung cấp dữ liệu và actionable insights để monitor các ứng dụng, hiểu và phản hồi với các thay đổi hiệu suất system-wide, tối ưu hóa việc sử dụng tài nguyên và có cái nhìn tổng thể về operational health.
   ![ConnectPrivate](/images/aws_s3.png)
   **Amazon S3 (Simple Storage Service)** là dịch vụ object storage được xây dựng để lưu trữ và truy xuất bất kỳ lượng dữ liệu nào từ bất cứ đâu. S3 cung cấp độ bền 99.999999999% (11 9's) và lưu trữ dữ liệu cho hàng triệu ứng dụng cho các công ty trên toàn thế giới. S3 cung cấp các tính năng quản lý đơn giản để có thể tổ chức dữ liệu và cấu hình access controls tinh tế.
   ![ConnectPrivate](/images/aws_sns.png)
   **Amazon SNS (Simple Notification Service)** là dịch vụ messaging được quản lý hoàn toàn cho cả application-to-application (A2A) và application-to-person (A2P) communication. SNS cung cấp các chủ đề (topics) cho high-throughput, push-based, many-to-many messaging giữa các hệ thống phân tán, microservices và event-driven serverless applications.
5. **Database & Data Processing**
   - **MongoDB**: Cơ sở dữ liệu NoSQL để lưu trữ dữ liệu ứng dụng
   - Kết nối với **AWS ecosystem** thông qua các managed services
