---
title: "Create IAM Policies"
date: "2025-06-21"
weight: 2
chapter: false
pre: " <b> 2.2 </b> "
---

### Understanding IAM Policies

ℹ️ **What is an IAM Policy?** An IAM Policy is a JSON document that defines permissions and access controls for AWS resources. These policies:

- Define precise permissions for AWS services and resources
- Can be attached to IAM Users, Groups, and Roles
- Follow the principle of least privilege
- Enable fine-grained access control

### Policy Assignment

ℹ️ **How Policies Work** IAM Policies provide the authorization framework by:

- Defining allowed and denied actions
- Specifying resource-level permissions
- Supporting both AWS managed and customer managed policies
- Enabling conditional access based on tags, time, or location

🔒 **Security Best Practices** When working with IAM Policies:

- Use AWS managed policies when possible
- Create custom policies only when necessary
- Regularly review and audit policy assignments
- Implement least privilege access

![VPC](/images/2.prerequisite/2.2/1.png)

### Steps to create policies

**Step 1:** Go to **AWS Console -> IAM**

**Step 2:** Select **Policies -> Create Policies**
![VPC](/images/2.prerequisite/2.2/2.png)

**Step 3:** Choose Policy editor: JSON and replace with the following JSON:
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
**Step 4:** Enter Policy Name: **WebsiteKMSPolicy** → Click **Create Policy**
[Policies](https:///images/2.prerequisite/2.2/3.png)
**Step 5:** Verify the created policy
[Policies](https:///images/2.prerequisite/2.2/4.png)
