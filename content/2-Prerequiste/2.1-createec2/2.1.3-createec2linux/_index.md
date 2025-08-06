---
title: "Create EC2 instance"
date: "2025-06-21"
weight: 3
chapter: false
pre: " <b> 2.1.3 </b> "
---

1. Go to [EC2 service management console](https://console.aws.amazon.com/ec2/v2/home)

- Click **Instances**.
- Click **Launch instances**.

![EC2](/images/2.prerequisite/027-createec2.png)

2. **Name**: Enter **Mern-stack EC2**.

3. Choose an Amazon Machine Image (AMI):

   - Select **Quick Start**.
   - Choose **Ubuntu**.
   - AMI: Select **Ubuntu Server 24.04 LTS**.

![EC2](/images/2.prerequisite/2.1/2.1.3/4.png)

4. Key Pair Configuration:

   - Click **Create key pair**.
   - Fill in the details as shown in the image.
     ![EC2](/images/2.prerequisite/2.1/2.1.3/2.png)

   **Security Note**: The key pair is essential for authenticating access to your EC2 instance. Store the .pem file securely and avoid sharing it. Losing the key pair may result in permanent loss of access to your instance.

5. Network Configuration

- Under **Network**, select **Mern-stack VPC**.
- Under **Subnet**, choose **Mern-stack Subnet**.
- Under **Auto-assign Public IP**, select **Use subnet setting (Enable)**.
  ![EC2](/images/2.prerequisite/2.1/2.1.3/3.png)

6. Review the settings and click Launch instance.

7. Once the instance is launched, click **View all instances** to check its details
   ![EC2](/images/2.prerequisite/2.1/2.1.3/5.png)
8. Wait for about 5 minutes until the Status check shows 2/2 checks passed and the instance state changes to Running.

**Pro Tip:** 2/2 checks passed status confirms that both the system check (performed by AWS) and the instance check (performed by the OS) were successful. This ensures your instance is ready for use.
