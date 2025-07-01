---
title: "Chuẩn bị VPC và EC2"
date: "2025-06-21"
weight: 1
chapter: false
pre: " <b> 2.1 </b> "
---

Trong bước này, chúng ta sẽ cần tạo một VPC có 2 subnet public / private. Sau đó tạo 1 EC2 Instance Linux nằm trong public subnet, 1 EC2 Instance Windows nằm trong private subnet.

Để tìm hiểu cách tạo các EC2 instance và VPC với public/private subnet các bạn có thể tham khảo bài lab :

- [Giới thiệu về Amazon EC2](https://000004.awsstudygroup.com/vi/)
- [Làm việc với Amazon VPC](https://000003.awsstudygroup.com/vi/)

### Nội dung

- [Tạo VPC](2.1.1-createvpc/)
- [Tạo Public subnet](2.1.2-createpublicsubnet/)
- [Tạo máy chủ Linux public](2.1.5-createec2linux/)
