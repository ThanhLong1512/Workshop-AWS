---
title: "Mã hóa dữ liệu với AWS KMS"
date: "2025-06-21"
weight: 1
chapter: false
pre: " <b> 4.1 </b> "
---

## Giới thiệu

**AWS Key Management Service (KMS)** cung cấp khả năng tạo và quản lý khóa mã hóa một cách tập trung, cho phép mã hóa dữ liệu cả khi lưu trữ (at rest) và trong quá trình truyền tải (in transit). Kết hợp với AWS Certificate Manager (ACM), hệ thống có thể tự động quản lý vòng đời của các chứng chỉ SSL/TLS, từ việc cấp phát, gia hạn đến triển khai across các dịch vụ AWS.

Đối với ứng dụng web được deploy trên EC2 với database MongoDB Atlas, việc implement mã hóa KMS đảm bảo rằng các thông tin như connection strings, user credentials, payment data, và personal information được bảo vệ ở mức độ enterprise. Điều này đặc biệt quan trọng khi ứng dụng xử lý dữ liệu cá nhân theo các quy định như GDPR, CCPA, hoặc luật An toàn thông tin mạng Việt Nam.

Thông qua việc tích hợp IAM roles và policies, EC2 instances có thể securely access KMS keys mà không cần hard-code credentials, tuân theo nguyên tắc least privilege và zero-trust security model. Kết hợp với CloudFront distribution sử dụng ACM certificates, toàn bộ traffic từ end-users đến application được mã hóa end-to-end, tạo nên một security perimeter toàn diện cho hệ thống.

## Các bước thực hiện

**Bước 1:** Truy cập **AWS Console -> AWS KMS -> Create Key**
![Visual Studio Code](/images/4.Security&Monitoring/4.1/3.png)
**Bước 2:** Chọn **"Symmetric"** và Key usage: **"Encrypt and decrypt"**
![Visual Studio Code](/images/4.Security&Monitoring/4.1/4.png)
**Bước 3:** Chọn **Role_ec2 -> Next**
![Visual Studio Code](/images/4.Security&Monitoring/4.1/5.png)
**Bước 4:** Kiểm tra lại policy của role đó đã đúng chưa
![Visual Studio Code](/images/4.Security&Monitoring/4.1/6.png)
**Bước 5:** Chọn **Finish** để tạo
![Visual Studio Code](/images/4.Security&Monitoring/4.1/7.png)
**Bước 6:** Thực hiện mở **Visual Studio Code -> AWS-BE**
![Visual Studio Code](/images/4.Security&Monitoring/4.1/1.png)
**Bước 7:** Mở **Terminal -> npm install aws-sdk**
![Visual Studio Code](/images/4.Security&Monitoring/4.1/2.png)
**Bước 8:** Tạo **kms.js** vào thư mục utils với nội dụng như sau:

{{< copyable title="kms.js" >}}
const AWS = require("aws-sdk");

AWS.config.update({
region: "ap-southeast-1"
});

const kms = new AWS.KMS();

class KMSService {
constructor() {
this.keyAlias = "alias/KMS-KEY";
}

async encrypt(plaintext) {
try {
console.log("Encrypting data...");

      const params = {
        KeyId: this.keyAlias,
        Plaintext: Buffer.from(plaintext, "utf8")
      };

      const result = await kms.encrypt(params).promise();
      const encrypted = result.CiphertextBlob.toString("base64");

      console.log("Data encrypted successfully");
      return encrypted;
    } catch (error) {
      console.error("Encryption failed:", error.message);
      throw error;
    }

}

async decrypt(encryptedData) {
try {
console.log("Decrypting data...");

      const params = {
        CiphertextBlob: Buffer.from(encryptedData, "base64")
      };

      const result = await kms.decrypt(params).promise();
      const decrypted = result.Plaintext.toString("utf8");

      console.log("Data decrypted successfully");
      return decrypted;
    } catch (error) {
      console.error("Decryption failed:", error.message);
      throw error;
    }

}

async encryptJSON(object) {
const jsonString = JSON.stringify(object);
return await this.encrypt(jsonString);
}

async decryptJSON(encryptedData) {
const decryptedString = await this.decrypt(encryptedData);
return JSON.parse(decryptedString);
}
}

module.exports = new KMSService();

{{< /copyable >}}
**Bước 9:** Thực hiện ghi 4 method bên dưới vào thư mục **models/AccountModel.js**

![Visual Studio Code](/images/4.Security&Monitoring/4.1/8.png)

**Bước 10:** Thực hiện gọi phương thức như hình bên dưới đối với dữ liệu là **AccountModel.js**

![Visual Studio Code](/images/4.Security&Monitoring/4.1/9.png)
