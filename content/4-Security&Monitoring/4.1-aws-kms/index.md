---
title: "Data encryption with AWS KMS "
date: "2025-06-21"
weight: 1
chapter: false
pre: " <b> 4.1 </b> "
---

## Introduction

**AWS Key Management Service (KMS)** provides centralized encryption key creation and management, enabling data encryption both at rest and in transit. When combined with AWS Certificate Manager (ACM), the system can automatically manage the lifecycle of SSL/TLS certificates, including issuance, renewal, and deployment across AWS services.

For web applications deployed on EC2 with MongoDB Atlas databases, implementing KMS encryption ensures that sensitive information such as connection strings, user credentials, payment data, and personal information is protected at an enterprise level. This is particularly critical for applications handling personal data under regulations like GDPR, CCPA, or Vietnam's Cybersecurity Law.

By integrating IAM roles and policies, EC2 instances can securely access KMS keys without hard-coding credentials, adhering to the principle of least privilege and a zero-trust security model. Combined with CloudFront distributions using ACM certificates, all traffic from end-users to the application is encrypted end-to-end, creating a comprehensive security perimeter for the system.

## Implementation Steps

**Step 1:** Navigate to **AWS Console -> AWS KMS -> Create Key**
![Visual Studio Code](/images/4.Security&Monitoring/4.1/3.png)
**Step 2:** Select **Symmetric** and Key Usage: **Encrypt and decrypt**
![Visual Studio Code](/images/4.Security&Monitoring/4.1/4.png)
**Step 3:** Choose **Role_ec2 -> Next**
![Visual Studio Code](/images/4.Security&Monitoring/4.1/5.png)
**Step 4:** Verify the role's policy is correctly configured
![Visual Studio Code](/images/4.Security&Monitoring/4.1/6.png)
**Step 5:** Click **Finish** to create the key
![Visual Studio Code](/images/4.Security&Monitoring/4.1/7.png)
**Step 6:** Open **Visual Studio Code -> AWS-BE**
![Visual Studio Code](/images/4.Security&Monitoring/4.1/1.png)
**Step 7:** Open **Terminal -> Run npm install aws-sdk**
![Visual Studio Code](/images/4.Security&Monitoring/4.1/2.png)
**Step 8:** Create **kms.js** in the utils folder with the following content::

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
**Step 9:** Implement the four methods below in **models/AccountModel.js**

![Visual Studio Code](/images/4.Security&Monitoring/4.1/8.png)

**Step 10:** Call the encryption/decryption methods as shown below for **AccountModel.js**

![Visual Studio Code](/images/4.Security&Monitoring/4.1/9.png)
