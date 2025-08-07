---
title: "Giám sát và thông báo tự động với CloudWatch và SNS"
date: "2025-06-21"
weight: 3
chapter: false
pre: " <b> 4.3 </b> "
---

## Giới thiệu

Trong môi trường cloud hiện đại, việc giám sát liên tục và phản ứng nhanh chóng với các sự cố là yếu tố then chốt quyết định sự thành công của ứng dụng. Amazon CloudWatch và Amazon Simple Notification Service (SNS) tạo thành một hệ thống giám sát và cảnh báo mạnh mẽ, cho phép bạn theo dõi hiệu suất ứng dụng 24/7 và nhận thông báo tức thì khi có bất thường xảy ra.

**Amazon CloudWatch - Đôi mắt của hạ tầng AWS**

- **Amazon CloudWatch** là dịch vụ giám sát và quan sát toàn diện, cung cấp khả năng theo dõi tất cả các tài nguyên AWS và ứng dụng của bạn

**Amazon SNS - Hệ thống thông báo đa kênh**

- **Amazon Simple Notification Service (SNS)** là messaging service hoàn toàn managed, cho phép gửi thông báo đến nhiều endpoint khác nhau

Với CloudWatch và SNS, bạn có thể xây dựng một hệ thống giám sát intelligent, tự động phát hiện anomalies và đảm bảo đội ngũ vận hành luôn được thông báo kịp thời về tình trạng hệ thống. Đây là foundation cho DevOps practices hiệu quả và reliable system operations.

## Các bước thực hiện

**Bước 1:** Truy cập **AWS Console -> CloudWatch**
![Visual Studio Code](/images/4.Security&Monitoring/4.3/1.png)
**Bước 2:** Chọn **Logs -> Log groups -> Create log group**
![Visual Studio Code](/images/4.Security&Monitoring/4.3/2.png)
**Bước 3:** Thực hiện cấu hình bên dưới:

- Log group name: **Mernstack-Cloudwatch**
- Retention setting: **1 days**
- Log class: **Standard**

**Bước 4:** Chọn **Create**
![Visual Studio Code](/images/4.Security&Monitoring/4.3/3.png)
**Bước 5:** Sau khi tạo thành công Log groups, truy cập **AWS Console -> WAF & Shield**

**Bước 6:** Chọn **Mernstack-WAF ->Logging and metrics**
![Visual Studio Code](/images/4.Security&Monitoring/4.3/4.png)
**Bước 7:** Chọn **Enable-> Logging destination**
![Visual Studio Code](/images/4.Security&Monitoring/4.3/5.png)
**Bước 8:** Chọn Log Groups mà bạn đã tạo, Redacted fields: **HTTP Method** sau đó chọn **Save**

**Bước 9:** Truy cập **AWS Console -> Simple Notification Service -> Next step**
![Visual Studio Code](/images/4.Security&Monitoring/4.3/6.png)
**Bước 10:** Thực hiện các cấu hình bên dưới

- Type: **Standard**
- Name: **Mernstack-SNS**

**Advanced options:**

- Delivery retry policy: **Default**
- Delivery status logging: **Disabled (for lab)**
- Encryption: **Disabled (for lab)**
- Access policy: **Default**
  ![Visual Studio Code](/images/4.Security&Monitoring/4.3/7.png)

**Bước 11:** Chọn **Create Topic** và sau đó kiểm tra kết quả
![Visual Studio Code](/images/4.Security&Monitoring/4.3/8.png)
**Bước 12:** Chọn **Create subscription**
![Visual Studio Code](/images/4.Security&Monitoring/4.3/9.png)
**Bước 13:** Chọn Protocol: **Email**, Endpoint: **nguyenboo2018@gmail.com**
![Visual Studio Code](/images/4.Security&Monitoring/4.3/10.png)
**Bước 14:** Chọn **Create Subscription**
![Visual Studio Code](/images/4.Security&Monitoring/4.3/11.png)
![Visual Studio Code](/images/4.Security&Monitoring/4.3/12.png)
**Bước 15:** Truy cập **AWS CloudWatch -> Alarm -> In Alarm -> Create alarm**
![Visual Studio Code](/images/4.Security&Monitoring/4.3/13.png)
**Bước 16:** Thực hiện các cấu hình bên dưới:

- Chọn **select metric -> EC2 -> Mernstack-EC2**
  ![Visual Studio Code](/images/4.Security&Monitoring/4.3/14.png)
- Chọn tương tự như hình bên dưới
  ![Visual Studio Code](/images/4.Security&Monitoring/4.3/15.png)
  ![Visual Studio Code](/images/4.Security&Monitoring/4.3/16.png)
- Đặt Alarm Name: **Mernstack-Alarm** sau đó chọn **Next -> Create Alarm**
  ![Visual Studio Code](/images/4.Security&Monitoring/4.3/17.png)
