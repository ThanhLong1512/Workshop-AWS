---
title: "Clean up resources"
date: 2026
weight: 5
chapter: false
pre: "<b>5. </b>"
---

We will perform the following steps to delete all the resources created in this exercise in the correct order to avoid dependency errors.

**Step 1: Remove Application Load Balancer (ALB)**

- Navigate to EC2 Management Console
- Select Load Balancers from the left menu
- Choose the created Application Load Balancer
- Click Actions → Delete
- Type "confirm" and click Delete

2. Delete Target Groups

- Go to Target Groups
- Select the target group created for ALB
- Click Actions → Delete
- Confirm with Yes, delete

**Step 2: Terminate EC2 Instances**

- In the EC2 Dashboard
- Select Instances
- Choose all instances (both public and private)
- Click Instance State → Terminate instance
- Confirm with Terminate

**Step 3: Delete other AWS Services**

**Delete CloudWatch and SNS**

1. Navigate to CloudWatch

- Select Alarms → choose created alarms → Delete
- Go to Log groups → select Log groups → Delete log group(s)

2. SNS Cleanup:

- Access SNS Console
- Select Topics → choose topic → Delete
- Go to Subscriptions → select subscription → Delete

3. Route 53:

- Access Route 53 Console
- Select Hosted zones
- Delete record sets first, then delete the hosted zone

4. Deleting KMS Keys

- Go to AWS KMS Console
- Select Customer managed keys
- Choose the key you created
- Click Key actions → Schedule key deletion
- Set waiting period (minimum 7 days)
- Confirm with Schedule deletion

5. WAF & Shield:

- Go to WAF & Shield Console
- Select Web ACLs
- Choose Web ACL → Delete
- Type "delete" to confirm

**Step 5: Remove CloudFront Distribution**

- Access CloudFront Console
- Select the distribution
- Click Disable and wait for status to change to "Disabled"
- Then click Delete

**Step 6: Xóa IAM Roles và Users**

- Navigate to IAM Console
- For Roles:
- Select created roles (SSM-Role, ECS-Role, etc.)
- Click Delete
- Enter role name to confirm
- For Policies:
- Filter by "Customer managed"
- Select policy → Actions → Delete

**Step 7: Remove Storage Resources**

S3 Buckets:

- Go to S3 Console
- Select the bucket
- Click Empty
- Type "permanently delete" → Empty
- Then click Delete bucket
- Enter bucket name to confirm

**Step 8: Remove Network Gateways**

1. NAT Gateway:

- Select NAT Gateways
- Choose NAT Gateway → Actions → Delete NAT gateway
- Type "delete" to confirm

2. Internet Gateway:

- Access Internet Gateways
- Select IGW → Actions → Detach from VPC
- Then Actions → Delete internet gateway

**Step 9: Final VPC Cleanup**

1. Delete Security Groups (except default):

- Select created security groups
  -Actions → Delete security group

2. Remove Subnets:

- Select all created subnets
- Actions → Delete subnet

3. Delete VPC:

- Select the Lab VPC
- Actions → Delete VPC
- Type "delete" to confirm

Important Notes
⚠️ Order Matters: Always delete dependent resources first

⚠️ Region Check: Verify you're working in the correct AWS Region.

⚠️ CloudFront: Disable before deleting (takes 15-20 minutes)

⚠️ Billing: Check AWS Billing Console to confirm no active resources

✅ Completion: After completing all steps, your AWS environment should be completely clean with no remaining resources from the lab. This ensures you won't incur any unexpected charges.
