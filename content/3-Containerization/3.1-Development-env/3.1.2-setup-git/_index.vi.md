---
title: "Thiết lập Git và Github Repository"
date: "2025-06-21"
weight: 2
chapter: false
pre: " <b> 3.1.2 </b> "
---

### Tổng quan về Git và Github Repository

![GitHub](/images/3.Containerization/3.1/3.1.2/1.png)

**GitHub** là một mạng xã hội đặc biệt dành cho lập trình viên, là một hệ thống quản lý dự án, lưu trữ source code, theo dõi và cộng tác trong các dự án phần mềm.Ngoài ra, **GitHub** là một dịch vụ nổi tiếng cung cấp kho lưu trữ mã nguồn Git cho các dự án phần mềm. Github có đầy đủ những tính năng của Git, ngoài ra nó còn bổ sung những tính năng về social để các developer tương tác với nhau.

**Git** là một hệ thống quản lý phiên bản phân tán (Distributed Version Control System – DVCS), nó là một trong những hệ thống quản lý phiên bản phân tán phổ biến nhất hiện nay. Git cung cấp cho mỗi lập trình viên kho lưu trữ (repository) riêng chứa toàn bộ lịch sử thay đổi.

1.  **Sự khác biệt giữa Git và GitHub**

    **Git** là hệ thống kiểm soát phiên bản mã nguồn mở được sử dụng phổ biến cho các dự án lớn và nhỏ.

    **GitHub** là Git Server, nơi mọi người chia sẻ và cộng tác trên mã nguồn họ tạo ra. GitHub sử dụng hệ thống kiểm soát phiên bản là Git. GitHub đơn giản hoá việc sử dụng Git mà không cần tới giao diện dòng lệnh

2.  **Vì sao nên sử dụng GitHub?**
    - Sử dụng phổ biến: Trong số các Github Server thì GitHub được coi là nền tảng phổ biến nhất và được ưa thích nhất với 4 triệu tổ chức và hơn 100 triệu nhà phát triển. Lý do ngoài việc sử dụng dễ dàng thì còn vì những tính năng như lưu trữ mã nguồn miễn phí, kiểm soát phiên bản phân tán, tạo project và tích hợp các nền tảng CI/CD phổ biến như Travis CI và Jenkins.
    - Cộng đồng đông đảo: GitHub có một cộng đồng các nhà phát triển lớn mạnh và năng động, khiến nó trở thành một nơi tuyệt vời để khám phá và đóng góp cho các dự án nguồn mở.
    - Bảo mật: Github cung cấp các tính năng như quét mã nguồn và phân tích dependency, giúp cải thiện tính bảo mật của mã nguồn.
    - Lưu trữ mã: GitHub cung cấp nền tảng để lưu trữ mã nguồn của bạn và cộng đồng nhà phát triển toàn cầu có thể truy cập được chúng một cách dễ dàng.
    - Hợp tác: Github tạo điều kiện cho sự hợp tác giữa các nhà phát triển bằng cách cho phép nhiều người có thể đồng thời đóng góp trên cùng một dự án.
3.  **Cách sử dụng GitHub**

    1. **Tạo một tài khoản GitHub**
       Nếu bạn chưa có tài khoản, hãy [truy cập trang chủ](https://github.com/) của GitHub và đăng ký tài khoản miễn phí. Sau khi nhập email và password, Github sẽ gửi cho bạn một email xác minh. Bạn cần mở email và click vào đường dẫn xác minh trong email để xác nhận địa chỉ email của bạn.
       ![GitHub](/images/3.Containerization/3.1/3.1.2/2.png)
       Sau khi tài khoản của bạn được xác minh, bạn có thể khám phá GitHub bằng cách trải nghiệm các tính năng của Github như duyệt qua các repository và các dự án công khai để hiểu những gì có sẵn.
    2. **Cài đặt và cấu hình Git**
       Nếu máy bạn chưa cài Git, bạn có thể làm theo [hướng dẫn cài đặt Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) và chọn cách phù hợp với hệ điều hành trên máy tính của bạn.
       Để kiểm tra, phiên bản Git bạn đã cài, bạn cần chạy lệnh
       ![GitHub](/images/3.Containerization/3.1/3.1.2/3.png)
    3. **Làm việc với repository**

       - **Tạo mới repository**
         Khi tạo mới repository, bạn cần phải đặt tên không trùng với tên của repository nào đã có trong danh sách repository của bạn và thêm mô tả cho repository.
         Mặc định, GitHub sẽ tạo repository công khai. Bạn có thể sửa chế độ của repository trước lúc tạo hoặc sau khi tạo thành công.
         ![GitHub](/images/3.Containerization/3.1/3.1.2/4.png)
         Sau khi bạn đã truy cập được chỗ tạo mới repository bạn giúp tôi tạo 2 repository với tên như sau: **AWS-FE và AWS-BE**

         Sau khi bạn đã hoàn tất việc tạo 2 repository, bạn ra trang **Home -> Avatar sát bên tay phải -> Your Repositories**
         ![GitHub](/images/3.Containerization/3.1/3.1.2/5.png)
         Nễu xuất hiện 2 repository bạn vừa mới tạo thì chúc mừng bạn đã tạo thành công
         ![GitHub](/images/3.Containerization/3.1/3.1.2/6.png)
