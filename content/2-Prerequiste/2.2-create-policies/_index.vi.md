---
title: "Tạo IAM Policies"
date: "2025-06-21"
weight: 2
chapter: false
pre: " <b> 2.2 </b> "
---

#### AWS Identity and Access Management (IAM) Policy

ℹ️ Tổng quan
AWS Identity and Access Management (IAM) Policy là tài liệu định nghĩa quyền truy cập chi tiết trong AWS. IAM Policy có thể được gán cho:

- IAM Groups (Nhóm người dùng)
- IAM Users (Người dùng)
- IAM Roles (Vai trò)

🔒 Cấu trúc và Phạm vi

IAM Policy bao gồm các thành phần chính:

- Effect: Cho phép (Allow) hoặc từ chối (Deny) quyền
- Action: Các hành động được phép thực hiện
- Resource: Tài nguyên AWS được áp dụng
- Condition: Điều kiện bổ sung (nếu có)

💡 Pro Tip: Luôn tuân thủ nguyên tắc đặc quyền tối thiểu khi tạo IAM Policy. Chỉ cấp những quyền cần thiết cho người dùng thực hiện công việc.

⚠️ Lưu ý quan trọng: Khi một IAM Policy được gán cho một đối tượng (User/Group/Role), các quyền sẽ có hiệu lực ngay lập tức. Hãy kiểm tra kỹ phạm vi quyền trước khi áp dụng.
![VPC](/images/2.prerequisite/2.2/1.png)

### Các bước thực hiện tạo Policies

**Bước 1:** Truy cập **AWS Console -> IAM**

**Bước 2:** Chọn **Policies -> Create Policy**
![Policies](/images/2.prerequisite/2.2/2.png)

**Bước 3:** Chọn **Policy editor: JSON** và thay thế json bên dưới
{{< copyable title="json" >}}
{
"Version": "2012-10-17",

    "Statement": [
        {
        "Sid": "KMSPermissions",
        "Effect": "Allow",
        "Action": [
            "kms:Encrypt",
            "kms:Decrypt",
            "kms:ReEncrypt*",
            "kms:GenerateDataKey*",
            "kms:DescribeKey"
        ],
        "Resource": "*",
        "Condition": {
            "StringEquals": {
            "kms:ViaService": "s3.ap-southeast-1.amazonaws.com"
            }
        }
        }
    ]

}
{{< /copyable >}}

**Bước 4:** Nhập Policy name: **WebsiteKMSPolicy** và sau đó chọn **Create Policy**

![Policies](/images/2.prerequisite/2.2/3.png)

**Bước 5:** Kiểm tra policy đã tạo

![Policies](/images/2.prerequisite/2.2/4.png)
