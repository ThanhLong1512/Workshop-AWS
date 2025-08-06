---
title: "Domain & DNS Configuration với Route53"
date: "2025-06-21"
weight: 3
chapter: false
pre: " <b> 3.3.2 </b> "
---

## Giới thiệu

Sau khi đã triển khai thành công website của bạn trên AWS thông qua các dịch vụ như EC2, bước tiếp theo quan trọng không kém là thiết lập domain và cấu hình DNS để người dùng có thể truy cập trang web của bạn thông qua một tên miền chuyên nghiệp. Amazon Route53 là dịch vụ DNS đáng tin cậy và mạnh mẽ của AWS, giúp bạn dễ dàng quản lý domain và chuyển hướng lưu lượng truy cập đến các tài nguyên web của bạn.

### Lợi ích việc sử dụng Route53

Amazon Route53 mang lại nhiều lợi ích vượt trội cho việc quản lý DNS và domain:

- **Độ tin cậy cao:** Route53 được xây dựng trên cơ sở hạ tầng toàn cầu của AWS, đảm bảo thời gian hoạt động (uptime) 99.99% và khả năng chịu lỗi cao.
- **Hiệu suất tối ưu:** Với mạng lưới máy chủ DNS phân tán trên toàn thế giới, Route53 sử dụng định tuyến dựa trên độ trễ (Latency-based Routing) để tự động chuyển hướng người dùng đến vị trí AWS gần nhất, giảm thiểu thời gian tải trang.
- **Tích hợp liền mạch:** Route53 hoạt động tốt với các dịch vụ AWS khác như EC2, S3, CloudFront và Load Balancer, giúp quá trình cấu hình trở nên đơn giản và thuận tiện.
- **Bảo mật mạnh mẽ:** Hỗ trợ DNSSEC (DNS Security Extensions) để bảo vệ chống lại các cuộc tấn công DNS spoofing, cùng với khả năng tích hợp AWS IAM để kiểm soát truy cập chi tiết.
- **Khả năng mở rộng:** Tự động xử lý lượng truy vấn DNS lớn mà không cần quản lý thủ công, phù hợp cho các website có lưu lượng truy cập biến động.
- **Quản lý tập trung:** Giao diện quản lý thống nhất trong AWS Console, cho phép bạn quản lý tất cả domain và bản ghi DNS ở một nơi.

### Các bước thực hiện

**Phương án 1: Đăng ký Domain trực tiếp trên AWS Route53**

- **Bước 1:** Truy cập **Route 53 -> Register a domain**
  ![Truy cập AWS Route 53](/images/3.Containerization/3.3/3.3.3/1.png)
- **Bước 2:** Nhập domain name mà bạn muốn đặt cho website, sau đó chọn mức giá phù hợp với bạn
  ![Tìm kiếm domain](/images/3.Containerization/3.3/3.3.3/2.png)
- **Bước 3:** Chọn Select với domain mà bạn muốn, sau đó tiến hành thanh toán
- **Bước 4:** Kiểm tra thanh toán thành công như hình bên dưới
  ![Tìm kiếm domain](/images/3.Containerization/3.3/3.3.3/3.png)
- **Bước 5:** Truy cập **Route 53 -> Create hosted zones**
- **Bước 6:** Nhập Domain name là tên miền mà bạn vừa đăng ký
  ![Tìm kiếm domain](/images/3.Containerization/3.3/3.3.3/4.png)
- **Bước 7:** Kết quả tạo hosted zones thành công như hình bên dưới
  ![Tìm kiếm domain](/images/3.Containerization/3.3/3.3.3/5.png)
- **Bước 8:** Chọn **Create record**
  - **Record 1: Record name: "", Value: IP EC2**
  - **Record 2: Record name: "www", Value: IP EC2**
    ![Tìm kiếm domain](/images/3.Containerization/3.3/3.3.3/6.png)
- **Bước 9:** Sau khi đã hoàn tất bước trên thì mất tối đa 2 giờ để DNS Propagation
- **Bước 10:** Tiến hành tải **Ngink trong EC2 Instances** với lệnh

        sudo apt update && sudo apt install nginx -y && sudo systemctl start nginx && sudo systemctl enable nginx

- **Bước 11:** Tiến hành tạo thư mục cấu hình Ngink

          sudo vim /etc/nginx/sites-available/mern-app

- **Bước 12:** Thêm cấu hình bên dưới vào thư mục Ngink
  {{< copyable title="ngink config" >}}
  server {
  listen 80;
  server_name cheese1512.com;

        location /api/ {
            proxy_pass http://localhost:8080/;
            proxy_http_version 1.1;
            proxy_set_header Upgrade $http_upgrade;
            proxy_set_header Connection 'upgrade';
            proxy_set_header Host $host;
            proxy_cache_bypass $http_upgrade;
        }

        location / {
            proxy_pass http://localhost:5173/;
            proxy_http_version 1.1;
            proxy_set_header Upgrade $http_upgrade;
            proxy_set_header Connection 'upgrade';
            proxy_set_header Host $host;
            proxy_cache_bypass $http_upgrade;
        }

  }
  {{< /copyable >}}

- **Bước 13:** Cài đặt Certbot cho SSL và bật Nginx site

        sudo apt install certbot python3-certbot-nginx -y
        sudo ln -s /etc/nginx/sites-available/mern-app /etc/nginx/sites-enabled/

- **Bước 14:** Kiểm tra & tải lại Nginx

        sudo nginx -t
        sudo systemctl reload nginx

- **Bước 15:** Yêu cầu chứng chỉ SSL và Xác minh DNS

        sudo certbot --nginx -d testing.integrationsninjas.com
        nslookup testing.integrationsninjas.com

- **Bước 16:** Sau khi mọi thứ diễn ra thành công thì bạn có thể truy cập domain name mà bạn muốn
- **Phương án 2: Sử dụng Domain từ một nhà cung cấp khác**

- **Bước 1:** Truy cập Hostinger tại đường [link](https://hpanel.hostinger.com) sau
- **Bước 2:** Chọn **Tên miền -> Nhận một tên miền mới**
  ![Tìm kiếm domain](/images/3.Containerization/3.3/3.3.3/7.png)
- **Bước 3:** Chọn tên miền phù hợp và tiến hành thanh toán
  ![Tìm kiếm domain](/images/3.Containerization/3.3/3.3.3/8.png)

- **Bước 4:** Sau khi đã thanh toán thành công
- **Bước 5:** Lặp lại từ **bước 10 - 15** ở phía trên và kiểm tra kết quả
