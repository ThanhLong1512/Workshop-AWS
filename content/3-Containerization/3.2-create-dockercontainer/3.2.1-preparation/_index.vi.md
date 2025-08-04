---
title: "Thiết lập môi trường để triển khai"
date: "2025-06-21"
weight: 1
chapter: false
pre: " <b> 3.2.1 </b> "
---

## Giới thiệu

Trước khi bắt đầu triển khai ứng dụng lên production, chúng ta cần chuẩn bị đầy đủ môi trường và các công cụ cần thiết. Việc thiết lập môi trường đúng cách sẽ giúp quá trình deployment diễn ra suôn sẻ và tránh các lỗi không mong muốn.

### Những gì chúng ta sẽ chuẩn bị

1. **Các Extensions cần thiết**
2. **Containerization Tools**
3. **CI/CD Pipeline**
4. **Tạo Repositories trên Docker Hub**

### Cách thực hiện

1. Thực hiện cài đặt các **Extensions** cần thiết
   - Bước 1: Bạn mở phần mềm **Visual Studio Code** sau đó nhấn tổ hợp phím **Ctrl+Shift+X**
   - Bước 2: Bạn tìm kiếm **Docker** sau đó nhấn **Install**
   - Bước 3: Lặp lại bước 2 với **GitHub Action**
   - Bước 4: Kiểm tra extension đã được cài đặt ở hình bên dưới
     ![Docker Extensions](/images/3.Containerization/3.2/3.2.1/2.png)
2. **Containerization Tools:**
   - Bước 1: Sau khi bạn đã thực hiện thành công phần **3.1.1** thì sau đó bạn giúp tôi mở **Docker Desktop** lên
   - Bước 2: Bạn truy cập theo chỉ dẫn hình bên dưới
     ![Docker Desktop Guide](/images/3.Containerization/3.2/3.2.1/3.png)
   - Bước 3: Chọn **Personal access token** --> **Generate new token**
     ![Docker Desktop Guide](/images/3.Containerization/3.2/3.2.1/5.png)
   - Bước 4: Điền thông tin **Docker Token Info** rồi sau đó chọn **Generate**
     ![Docker Desktop Guide](/images/3.Containerization/3.2/3.2.1/4.png)
   - Bước 5: Lưu lại 2 thông tin bên dưới hình để tiếp tục cho quá trình chuẩn bị tiếp theo
     ![Docker Desktop Guide](/images/3.Containerization/3.2/3.2.1/6.png)
3. **CI/CD Pipeline:**
   - Bước 1: Mở GitHub và thực hiện đăng nhập tài khoản của bạn
   - Bước 2: Vào repository mà bạn đã tạo tên là **AWS-FE**
   - Bước 3: Tiếp theo sẽ vào mục **Settings -> Secrets and variables -> Action**
   - Bước 4: Chọn **New repository secret**
   - Bước 5: Name: **DOCKER_USERNAME** và Secret: **thanhlep**
   - Bước 6: Tương tư với **DOCKER_PASSWORD**
     ![Docker Desktop Guide](/images/3.Containerization/3.2/3.2.1/7.png)
4. **Tạo Repositories trên Docker Hub**

   - Bước 1: Đăng nhập tài khoản của bạn trên **Docker Hub**
   - Bước 2: Chọn **Repositories -> Create a repository**
     ![Docker Desktop Guide](/images/3.Containerization/3.2/3.2.1/8.png)
   - Bước 3: Repository name: **reactjs-web** và Visibility: **Public**
   - Bước 4: Tạo tương tự đối với **nodejs-web**
     ![Docker Desktop Guide](/images/3.Containerization/3.2/3.2.1/9.png)
