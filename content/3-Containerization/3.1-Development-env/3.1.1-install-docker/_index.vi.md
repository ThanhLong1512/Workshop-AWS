---
title: "Cài đặt Docker Desktop"
date: "2025-06-21"
weight: 1
chapter: false
pre: " <b> 3.1.1 </b> "
---

### Tổng quan về Docker

![Docker](/images/3.Containerization/3.1/3.1.1/1.png)

**Docker** là một nền tảng cho developers và sysadmin để develop, deploy và run application với container. Nó cho phép tạo các môi trường độc lập và tách biệt để khởi chạy và phát triển ứng dụng và môi trường này được gọi là container. Khi cần deploy lên bất kỳ server nào chỉ cần run container của Docker thì application của bạn sẽ được khởi chạy ngay lập tức.

**Các thành phần chính của Docker**

![Docker](/images/3.Containerization/3.1/3.1.1/2.png)

**Nguyên tắc hoạt động của Docker**

![Docker](/images/3.Containerization/3.1/3.1.1/3.png)

1.  **Containerization** là gì?

    **Containerization** là một công nghệ ảo hoá, giúp giải quyết vấn đề này bằng cách đóng gói ứng dụng và tất cả các phụ thuộc (dependencies) của nó (như thư viện, cấu hình) vào một đơn vị độc lập gọi là container. Container này đảm bảo rằng phần mềm sẽ chạy ổn định và nhất quán trên bất kỳ môi trường nào, dù là trên máy tính cá nhân của Developer, Test Server, hay môi trường Production trên cloud.

    - Trước khi có container: Developer viết một ứng dụng trên máy tính cá nhân sử dụng thư viện Python phiên bản 3.6. Sau khi kiểm thử thành công, anh ấy triển khai ứng dụng này lên máy chủ Production, nhưng máy chủ này lại đang chạy Python phiên bản 3.7. Sự khác biệt nhỏ này đã gây ra lỗi do một số thư viện không tương thích với Python 3.7.

    - Với container: Developer có thể đóng gói ứng dụng của mình cùng với tất cả các thư viện, bao gồm phiên bản Python 3.6 mà ứng dụng cần, vào một container. Khi container này được triển khai trên bất kỳ môi trường nào (local, test, production), ứng dụng vẫn sẽ hoạt động chính xác như khi nó được kiểm thử trên máy tính cá nhân.

2.  Vai trò của **Containerization**

- **Consistency (Nhất quán)**: Đảm bảo rằng ứng dụng được đóng gói trong container sẽ hoạt động giống nhau trên mọi môi trường, dù là trên máy tính của developer, test server, hay môi trường production.

- **Portability (Di động)**: container là các gói phần mềm nhẹ có thể dễ dàng chuyển từ hệ thống này sang hệ thống khác mà không gặp vấn đề về tương thích.

- **Scalability (Khả năng mở rộng)**: Containers có thể được khởi động hoặc dừng nhanh chóng, cho phép các ứng dụng dễ dàng mở rộng hoặc thu hẹp tùy theo nhu cầu sử dụng thực tế.

- **Efficiency (Hiệu quả)**: Container chia sẻ kernel của hệ điều hành chủ, không giống như các máy ảo truyền thống phải có một hệ điều hành đầy đủ riêng. Điều này làm cho container tốn ít tài nguyên hơn, khởi động nhanh hơn và có ít chi phí quản lý hơn.

- **Isolation (Cô lập)**: Container đảm bảo rằng các ứng dụng được cô lập với nhau, tăng cường bảo mật. Nếu một ứng dụng bị tấn công, sự cố này không ảnh hưởng đến các ứng dụng khác.

### Hướng dẫn cài đặt và sử dụng Docker

{{%notice warning%}}
Hướng dẫn này chỉ dành cho hệ điều hành **Windows**.

- Nếu bạn đang sử dụng macOS hoặc một hệ điều hành nào khác, vui lòng tìm tài liệu hướng dẫn phù hợp, vì các bước cài đặt và yêu cầu hệ thống có thể khác biệt đáng kể.

- Kiểm tra lại hệ điều hành của bạn trước khi tiếp tục để tránh lỗi hoặc cài đặt không tương thích.
  {{%/notice%}}

1. Tải ứng dụng Docker Desktop tại đường [link](https://docs.docker.com/desktop/setup/install/windows-install/), lưu ý nếu máy tính của bạn dùng chip ARM thì chúng ta sử dụng phiên bản dưới, nếu sử dụng chip x86/x64 của Intel và AMD thì tải phiên bản trên.

![Docker](/images/3.Containerization/3.1/3.1.1/4.png)

2. Double click vào file **Docker Desktop Installer.exe** đã download ở bước 1 để bắt đầu cài đặt. Mặc định, **Docker Desktop** được cài đặt tại đường dẫn **C:\Program Files\Docker\Docker.** và sau đó nhấn **OK** để tải

![Docker](/images/3.Containerization/3.1/3.1.1/85.png)

3. Sau khi hoàn tất cài đặt thì nhấn **Close and Restart**
4. Vào CMD và gõ **wsl** nếu xuất hiện tương tự như hình ảnh bên dưới thì bạn đã thành công

![Docker](/images/3.Containerization/3.1/3.1.1/6.png)
