---
title: "Hướng dẫn clone dự án FE&BE và đẩy lên Github Repository"
date: "2025-06-21"
weight: 2
chapter: false
pre: " <b> 3.1.3 </b> "
---

Sau khi bạn đã có 2 repository trong tài khoản GitHub của bạn, bạn giúp tôi tải phần mềm sau: [Visual Studio Code](https://code.visualstudio.com/) và [GitHub Desktop](https://desktop.github.com/download/) để thuận lợi trong việc clone dự án và đẩy lên GitHub Repository diễn ra nhanh hơn thì sau đây tôi sẽ giới thiệu sơ qua về 2 phần mềm đó

1. **Visual Studio Code là gì**
   ![VSCODE](/images/3.Containerization/3.1/3.1.3/2.png)

   **Visual Studio Code (VS Code)** là một trình soạn thảo mã nguồn miễn phí, đa nền tảng, được phát triển bởi Microsoft. Nó đã nhanh chóng trở thành một trong những trình soạn thảo phổ biến nhất dành cho các nhà phát triển, nhờ giao diện thân thiện, tính năng mạnh mẽ và khả năng mở rộng cao.

   **Lý do nên chọn Visual Studio Code?**

   - Miễn phí và mã nguồn mở: VS Code hoàn toàn miễn phí và được cấp phép theo giấy phép MIT. Điều này nghĩa là bạn có thể sử dụng và sửa đổi nó tự do mà không phải trả bất kỳ khoản phí nào. Bạn thậm chí có thể đóng góp vào dự án bằng cách sửa lỗi, thêm tính năng mới hoặc dịch thuật. Điều này đã thu hút rất nhiều lập trình viên và đóng góp vào sự phát triển mạnh mẽ của VS Code.
   - Đa nền tảng: VS Code có sẵn trên Windows, macOS và Linux, cho phép bạn sử dụng nó trên bất kỳ hệ điều hành nào. Điều này mang lại sự thuận tiện cho các lập trình viên khi họ có thể làm việc trên nhiều thiết bị khác nhau mà không cần thay đổi môi trường phát triển.
   - Giao diện thân thiện: VS Code có giao diện đơn giản, dễ sử dụng và trực quan, phù hợp cho cả người mới bắt đầu và các nhà phát triển có kinh nghiệm.
   - Hỗ trợ nhiều ngôn ngữ lập trình: VS Code hỗ trợ hơn 30 ngôn ngữ lập trình phổ biến, bao gồm JavaScript, Python, Java, C++, C#, Golang, PHP và nhiều hơn nữa. Bạn có thể sử dụng VS Code để viết mã cho bất kỳ dự án nào, bất kể ngôn ngữ lập trình nào bạn đang sử dụng. VS Code cung cấp hỗ trợ cú pháp, gợi ý mã thông minh và các tính năng gỡ lỗi cho mỗi ngôn ngữ, giúp bạn viết mã hiệu quả và dễ dàng hơn.Ví dụ: Đối với JavaScript: VS Code cung cấp hỗ trợ hoàn chỉnh cho JavaScript, bao gồm IntelliSense (gợi ý mã thông minh), hỗ trợ gỡ lỗi tích hợp, hỗ trợ TypeScript.

2. **GitHub Desktop là gì ?**

   ![GitHub Desktop](/images/3.Containerization/3.1/3.1.3/1.png)

   **GitHub Desktop** đóng vai trò là cầu nối cho những người thích giao diện đồ họa hơn là thao tác dòng lệnh. Nó hợp lý hóa quy trình làm việc của Git, từ việc sao chép kho lưu trữ đến đẩy thay đổi và tích hợp các tính năng bổ sung như tô sáng cú pháp và xem xét mã để tạo điều kiện cho sự cộng tác và nâng cao năng suất.

   **Ưu điểm và Nhược điểm**

   - **Ưu điểm của GitHub Desktop**

     - Thiết kế trực quan: Đơn giản hóa việc điều hướng, cam kết và quản lý nhánh để mang lại trải nghiệm mượt mà cho người dùng.
     - Tích hợp GitHub: Cung cấp quy trình làm việc liền mạch để quản lý kho lưu trữ và cộng tác trực tiếp với GitHub.
     - Hợp tác hợp lý: Nâng cao nỗ lực của nhóm với việc xem xét mã, thảo luận và đóng góp dễ dàng cho các dự án GitHub.
     - Cập nhật tự động: Tự động cập nhật các tính năng mới nhất và cải tiến bảo mật cho ứng dụng.

   - **Nhược điểm của GitHub Desktop**

     - Không có hỗ trợ Linux chính thức: Việc không có phiên bản Linux chính thức có thể dẫn đến những thách thức về khả năng tương thích và cập nhật
     - Bộ tính năng cơ bản: Có thể không đủ cho người dùng tìm kiếm các chức năng Git nâng cao như rebase tương tác hoặc biểu đồ cam kết chi tiết.
     - Giới hạn đối với quy trình làm việc phức tạp: Những người có dự án phức tạp có thể thấy khả năng của GitHub Desktop có phần hạn chế.
     - Tập trung vào GitHub: Được tối ưu hóa cho GitHub, điều này có thể hạn chế tiện ích của GitHub đối với các dự án được lưu trữ trên các nền tảng khác.

### Cách clone dự án FE&BE và đẩy lên Github Repository

1. **Bước 1:** Bạn truy cập mẫu 2 repository FE&BE từ 2 đường link sau: [FE Repository](https://github.com/ThanhLong1512/FE-Dentist) và [BE repository](https://github.com/ThanhLong1512/BE-Dentist).
2. **Bước 2:** Copy đường dẫn từ BE repository và sau đó mở **GitHub Desktop** lên.
   ![GitHub Desktop](/images/3.Containerization/3.1/3.1.3/3.png)
3. **Bước 3:** Sau khi mở Github Desktop thành công sau đó bạn vào **File -> Clone a repository -> URL**.
   ![GitHub Desktop](/images/3.Containerization/3.1/3.1.3/4.png)
4. **Bước 4:** Bạn dán đường dẫn repository mà bạn đã copy vào ô input đầu tiên và tạo một folder mà bạn muốn lưu.
   ![GitHub Desktop](/images/3.Containerization/3.1/3.1.3/5.png)
5. **Bước 5:** Sau khi bạn clone thành công thì bạn tiếp tục mở Visual Studio Code.
6. **Bước 6:** Chọn **File -> Open folder to start working -> Chọn thư mục mà bạn đã clone về**.
   ![GitHub Desktop](/images/3.Containerization/3.1/3.1.3/6.png)
7. **Bước 7:** Sau khi đã xuất hiện các thư mục mà dự án bạn đã clone tiếp tục bạn chọn **Terminal -> New Terminal** rồi sau đó bạn chạy lệnh **npm install**.
   ![GitHub Desktop](/images/3.Containerization/3.1/3.1.3/7.png)
8. **Bước 8:** Chạy tiếp tục lệnh **npm run start** và nếu xuất hiện giống hình ảnh bên dưới thì chúc mừng bạn.
   ![GitHub Desktop](/images/3.Containerization/3.1/3.1.3/8.png)
9. **Bước 9:** Tiếp tục sẽ đẩy project này lên repository mà bạn đã tạo
10. **Bước 10:** Bạn gõ lệnh **git remote remove origin** để xóa remote cũ từ repository mà bạn đã clone.
11. **Bước 11:** Sau đó bạn mở repository **AWS-BE** và copy đường dẫn ở hình bên dưới và đưa vào terminal.
    ![GitHub Desktop](/images/3.Containerization/3.1/3.1.3/9.png)
12. **Bước 12:** Sau khi tiếp tục gõ lệnh **git push -u origin main** và sau đó ra reload lại trang và nếu xuất hiện hình bên dưới thì chúc mừng bạn.
    ![GitHub Desktop](/images/3.Containerization/3.1/3.1.3/10.png)
13. **Bước 13:** Lặp lại từ **B2 -> B12** cho FE
