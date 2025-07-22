---
title: "Tạo Docker Containers"
date: "2025-06-21"
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

![Docker](/images/3.Containerization/3.2/1.png)
**Giới thiệu Docker và Containerization?**
Docker là một platform containerization cho phép đóng gói ứng dụng và tất cả dependencies vào một container nhẹ, portable và isolated. Container có thể chạy nhất quán trên bất kỳ môi trường nào.

**Tại sao sử dụng Docker?**

- **Consistency**: Đảm bảo ứng dụng chạy giống nhau trên mọi môi trường.
- **Portability**: Dễ dàng deploy từ development đến production.
- **Efficiency**: Sử dụng tài nguyên hiệu quả hơn VMs.
- **Scalability**: Dễ dàng scale các service.

**Chuẩn bị**:

1. **Bước 1**: Để đảm bảo bạn đã cài đặt Docker hãy dán lệnh đó vào bash để kiểm tra phiên bản docker trong máy bạn
   {{< copyable >}}
   docker --version
   {{< /copyable >}}
2. **Bước 2**: Nếu bạn chưa cài đặt Docker thì đây là [video hướng dẫn cài đặt Docker](https://www.youtube.com/watch?v=bw-bMhlhcpg)
3. **Bước 3**: Kiểm tra kết quả nếu bạn xuất hiện tương tự như hình ảnh bên dưới thì chúc mừng bạn
   ![Docker](/images/3.Containerization/3.2/2.png)

### Nội dung:

- [Viết Dockerfile cho Frontend (React.js)](./3.2.1-dockerfile-FE//)
- [Viết Dockerfile cho Backend (Node.js/Express)](./3.2.2-dockerfile-BE//)a
- [Build và test containers locally](./3.2.3-test-containers//)
