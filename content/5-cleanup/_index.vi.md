---
title: "Dọn dẹp tài nguyên  "
date: 2026
weight: 5
chapter: false
pre: "<b>5. </b>"
---

Chúng ta sẽ tiến hành các bước sau để xóa toàn bộ các tài nguyên đã tạo trong bài thực hành này theo đúng thứ tự để tránh lỗi phụ thuộc.

**Bước 1: Dừng và xóa ALB (Application Load Balancer)**

1. **Truy cập giao diện quản trị EC2**

- Click **Load Balancers** trong menu bên trái
- Chọn Application Load Balancer đã tạo
- Click **Actions → Delete**
- Xác nhận bằng cách gõ "confirm" và click **Delete**

2. **Xóa Target Groups**

- Click **Target Groups**
- Chọn target group đã tạo cho ALB
- Click Actions → **Delete**
- Click **Yes**, delete để xác nhận

**Bước 2: Xóa EC2 Instances**

**1. Xóa EC2 Instances**

- Truy cập giao diện **EC2**
- Click **Instances**
- Chọn tất cả instances (cả public và private)
- Click Instance State → **Terminate instance**
- Click **Terminate** để xác nhận

**Bước 3: Xóa các AWS Services khác**

**Xóa CloudWatch và SNS**

**1. Truy cập CloudWatch**

- Click **Alarms → chọn các alarm đã tạo → Delete**
- Click **Log groups → chọn Log groups → Delete log group(s)**

**2. Truy cập SNS**

- Click **Topics → chọn topic → Delete**
- Click **Subscriptions → chọn subscription → Delete**

**3. Xóa Route 53**

- Truy cập **Route 53**
- Click **Hosted zones**
- Chọn hosted zone (trừ các bản ghi mặc định)
- Xóa các record set trước, sau đó xóa hosted zone

**4. Xóa KMS và WAF**

- Truy cập **KMS**
- Click Customer managed keys
- Chọn key đã tạo → Key actions → Schedule key deletion
- Chọn thời gian chờ (tối thiểu 7 ngày) → **Schedule deletion**

**5. Truy cập WAF**

- Click **Web ACLs**
- Chọn **Web ACL → Delete**
- Gõ "delete" để xác nhận

**Bước 5: Dọn dẹp CloudFront**

- Truy cập **CloudFront**
- Chọn distribution đã tạo
- Click Disable và chờ status chuyển thành "Disabled"
- Sau đó click **Delete**

**Bước 6: Xóa IAM Roles và Users**

**1. Truy cập IAM**

- Click **Roles**
- Tìm kiếm và chọn các role đã tạo (SSM-Role, ECS-Role, etc.)
- Click **Delete** cho từng role
- Điền tên role để xác nhận

**2. Xóa IAM Users**

- Click **Users**
- Chọn user đã tạo (Portfwd, etc.)
- Click **Delete user**
- Điền tên user để xác nhận

**3. Xóa IAM Policies (custom)**

- Click **Policies**
- Filter theo "Customer managed"
- **Chọn policy đã tạo → Actions → Delete**

**Bước 7: Xóa S3 Bucket**

**1. Truy cập S3**

- Chọn bucket đã tạo
- Click **Empty**
- Gõ "permanently delete" → Empty
- Click **Exit**

**2. Xóa bucket**

- Click **Delete**
- Gõ tên bucket để xác nhận → **Delete bucket**

**Bước 8: Xóa Internet Gateway và NAT Gateway**

**1. Xóa NAT Gateway trước**

- Click NAT Gateways
- Chọn NAT Gateway → Actions → Delete NAT gateway
- Gõ "delete" để xác nhận

**2. Giải phóng Elastic IP**

- Click Elastic IPs
- Chọn EIP đã tạo → Actions → Release Elastic IP address

**3. Detach và xóa Internet Gateway**

- Click **Internet Gateways**
- Chọn IGW → Actions → Detach from VPC
- Sau đó **Actions → Delete internet gateway**

**Bước 9: Xóa VPC và các thành phần liên quan**

**1. Xóa Security Groups (trừ default)**

- Click **Security Groups**
- Chọn các security group đã tạo (không chọn default)
- Chọn **Actions → Delete security group**

**2. Xóa Route Tables (trừ main)**

- Click **Route Tables**
- Chọn route table đã tạo (không chọn main)
- Click **Actions → Delete route table**

**3. Xóa Subnets**

- Click **Subnets**
- Chọn tất cả subnet đã tạo
- Click **Actions → Delete subnet**

**4. Xóa VPC**

- Click **Your VPCs**
- Chọn VPC đã tạo (Lab VPC)
- Click **Actions → Delete VPC**
- Gõ "delete" để xác nhận

Lưu ý quan trọng

⚠️ Thứ tự xóa rất quan trọng: Phải xóa theo thứ tự từ các tài nguyên phụ thuộc đến tài nguyên chính để tránh lỗi.

⚠️ Kiểm tra Region: Đảm bảo đang làm việc ở đúng AWS Region chứa các tài nguyên.

⚠️ CloudFront: Cần disable trước khi xóa và có thể mất 15-20 phút để hoàn tất.

⚠️ Billing: Kiểm tra AWS Billing Console để đảm bảo không còn tài nguyên nào đang tính phí.

✅ Hoàn tất: Sau khi thực hiện xong tất cả các bước, hãy chờ 5-10 phút rồi kiểm tra lại từng service để đảm bảo đã xóa sạch.
