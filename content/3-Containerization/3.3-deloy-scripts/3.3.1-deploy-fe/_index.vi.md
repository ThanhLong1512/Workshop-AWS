---
title: "Tạo scripts để deploy ứng dụng React.js"
date: "2025-06-21"
weight: 1
chapter: false
pre: " <b> 3.2.1 </b> "
---

### Giới thiệu

Việc deploy ứng dụng React.js lên production server là một quá trình phức tạp với nhiều bước cần thực hiện chính xác. Thay vì làm thủ công từng bước - dễ dẫn đến sai sót và mất thời gian, chúng ta sẽ tạo các scripts tự động hóa toàn bộ quá trình này.
Scripts deployment giúp đảm bảo tính nhất quán, giảm thiểu lỗi human error và cho phép deploy nhanh chóng, đáng tin cậy. Đặc biệt quan trọng khi cần deploy nhiều lần hoặc trên nhiều môi trường khác nhau.
Trong thực tế production, một quy trình deploy Node.js chuẩn cần bao gồm: setup môi trường server, cài đặt dependencies, cấu hình web server (Nginx), thiết lập SSL, quản lý process và monitoring. Mỗi bước đều có những chi tiết kỹ thuật riêng và cần được thực hiện theo đúng thứ tự.

### Lợi ích của việc script hóa deployment

- **Tính nhất quán:** Mỗi lần deploy đều thực hiện chính xác các bước giống nhau, loại bỏ sự khác biệt giữa các lần deploy và đảm bảo môi trường production ổn định.
- **Tiết kiệm thời gian:** Tự động hóa các tác vụ lặp đi lặp lại, giảm thời gian deploy từ hàng giờ xuống còn vài phút.
- **Giảm thiểu lỗi:** Loại bỏ human error thường xảy ra khi thực hiện thủ công nhiều bước phức tạp.
- **Khả năng rollback:** Có thể nhanh chóng quay lại phiên bản trước khi gặp vấn đề.
- **Tái sử dụng:** Scripts có thể được customize và sử dụng cho multiple projects và environments.

### Quy trình thực hiện

- **Bước 1:** Truy cập vào **EC2 -> Instances** .

- **Bước 2:** Chọn **instances đã tạo -> Connect -> Connect**

  ![Kết nối Instance](/images/3.Containerization/3.3/3.3.2/1.png)

- **Bước 3:** Copy dòng lệnh và chạy lệnh **sudo apt-get update && sudo apt-get install docker.io -y && sudo systemctl start docker && sudo chmod 666 /var/run/docker.sock && sudo systemctl enable docker && docker --version** và sau đó chạy lệnh **docker ps** để kiểm tra cài đặt
  ![Cài đặt Docker trên Ubuntu](/images/3.Containerization/3.3/3.3.2/2.png)

- **Bước 4:** Truy cập GitHub và vào dự án **AWS-FE**, sau đó chọn **Settings -> Runner -> New self-hosted runner**

  ![Truy cập Runner trong Github](/images/3.Containerization/3.3/3.3.1/1.png)

- **Bước 5:** Chọn Runner image: **Linux** và sau đó sao chép các lệnh dưới đây vào **EC2 Instances**

  ![Truy cập Runner trong Github](/images/3.Containerization/3.3/3.3.1/2.png)

- **Bước 6:** Sau khi chạy xong các lệnh trên, chạy thêm 2 lệnh bên dưới

{{< copyable title="ec2" >}}
sudo ./svc.sh install
sudo ./svc.sh start

{{< /copyable >}}

- **Bước 7:** Sau khi đã chạy thành công các lệnh trên, kiểm tra runner hoạt động như hình bên dưới
  ![Truy cập Runner trong Github](/images/3.Containerization/3.3/3.3.2/5.png)
- **Bước 8:** Truy cập **Visual Studio Code** sau đó mở project **AWS-Fe**
- **Bước 9:** Thực hiện push code lên GitHub,sau đó vào mục **Actions** trong GitHub và chờ đợi quá trình deploy
- **Bước 10:** Kiểm tra quá trình deploy thành công như hình bên bên dưới
  ![Truy cập Runner trong Github](/images/3.Containerization/3.3/3.3.1/3.png)
- **Bước 11:** Sau khi quá trình deploy đã thành công thì kiểm tra **Public IP EC2:5173**
  ![Truy cập Runner trong Github](/images/3.Containerization/3.3/3.3.1/4.png)
