---
title: "Deploy Scripts"
date: "2025-06-21"
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

### Tổng quan

Sau khi đã hoàn thành việc containerization ứng dụng với Docker và thiết lập CI/CD pipeline với GitHub Actions, bước tiếp theo là tạo ra các deploy scripts để tự động hóa quá trình triển khai ứng dụng lên các môi trường khác nhau.
Deploy scripts là những script tự động hóa giúp đơn giản hóa việc deployment, từ việc pull Docker images, stop/start containers, đến việc kiểm tra health check và rollback khi cần thiết. Điều này đặc biệt quan trọng khi bạn cần deploy thường xuyên hoặc có nhiều môi trường khác nhau (development, staging, production).

#### Lợi ích của Deploy Scripts

- **Tự động hóa hoàn toàn**: Giảm thiểu các bước manual và human errors trong quá trình deployment.
- **Consistency**: Đảm bảo quá trình deployment được thực hiện nhất quán trên tất cả các môi trường.
- **Rollback nhanh chóng**: Có thể quay lại phiên bản trước đó một cách nhanh chóng khi gặp sự cố.
- **Environment Management**: Quản lý các biến môi trường và cấu hình khác nhau cho từng environment.
- **Health Checking**: Tự động kiểm tra ứng dụng sau khi deploy để đảm bảo hoạt động bình thường.

#### Kiến trúc Deploy Scripts

Trong phần này, chúng ta sẽ tạo deploy scripts cho cả Frontend (React.js) và Backend (Node.js) với các tính năng:

- **Environment Detection**: Tự động detect và áp dụng cấu hình phù hợp cho từng môi trường
- **Docker Management**: Tự động pull images, manage containers, và cleanup resources
- **Health Monitoring**: Kiểm tra trạng thái ứng dụng sau deployment
- **Logging & Notification**: Ghi log chi tiết và thông báo kết quả deployment
- **Rollback Mechanism**: Khả năng rollback về version trước khi có lỗi

### Nội dung

1.  [Tạo scripts để deploy ứng dụng React.js](3.3.1-deploy-fe/)
2.  [Tạo scripts để deploy ứng dụng Node.js](3.3.2-deploy-be/)
3.  [Domain & DNS Configuration với Route 53](3.3.3-domain-route53/)
