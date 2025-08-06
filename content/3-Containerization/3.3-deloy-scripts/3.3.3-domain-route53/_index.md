---
title: "Domain & DNS Configuration with Route53"
date: "2025-06-21"
weight: 3
chapter: false
pre: " <b> 3.3.2 </b> "
---

## Introduction

After successfully deploying your website on AWS using services like EC2, the next crucial step is setting up a domain and configuring DNS so users can access your website through a professional domain name. Amazon Route53 is AWS's reliable and powerful DNS service, making it easy to manage domains and direct traffic to your web resources.

### Benefits of Using Route53

Amazon Route53 offers several advantages for DNS and domain management:

- **High Reliability:** Built on AWS's global infrastructure, Route53 ensures 99.99% uptime and high fault tolerance.

- **Optimized Performance:** With a distributed network of DNS servers worldwide, Route53 uses Latency-based Routing to automatically direct users to the nearest AWS location, reducing page load times.

- **Seamless Integration:** Works smoothly with other AWS services like EC2, S3, CloudFront, and Load Balancer, simplifying configuration.

- **Strong Security:** Supports DNSSEC (DNS Security Extensions) to protect against DNS spoofing attacks and integrates with AWS IAM for fine-grained access control.

- **Scalability:** Automatically handles large DNS query volumes without manual management, ideal for websites with fluctuating traffic.

- **Centralized Management:** A unified interface in AWS Console allows you to manage all domains and DNS records in one place.

### Implementation Steps

**Option 1: Register a Domain Directly on AWS Route53**

- **Step 1:** Go to **Route 53 -> Register a domain**
  ![Truy cập AWS Route 53](/images/3.Containerization/3.3/3.3.3/1.png)
- **Step 2:** Enter your desired domain name and choose a suitable pricing plan
  ![Tìm kiếm domain](/images/3.Containerization/3.3/3.3.3/2.png)
- **Step 3:** Select the domain you want and proceed to checkout
- **Step 4:** Verify successful payment as shown below
  ![Tìm kiếm domain](/images/3.Containerization/3.3/3.3.3/3.png)
- **Step 5:** Go to **Route 53 -> Create hosted zones**
- **Step 6:** Enter the domain name you just registered
  ![Tìm kiếm domain](/images/3.Containerization/3.3/3.3.3/4.png)
- **Step 7:** Successful hosted zone creation should look like this:
  ![Tìm kiếm domain](/images/3.Containerization/3.3/3.3.3/5.png)
- **Step 8:** Select **Create record**
  - **Record 1: Record name: "", Value: IP EC2**
  - **Record 2: Record name: "www", Value: IP EC2**
    ![Tìm kiếm domain](/images/3.Containerization/3.3/3.3.3/6.png)
- **Step 9:** DNS propagation may take up to 2 hours.
- **Step 10:** Install **Nginx on EC2 Instances** with:

        sudo apt update && sudo apt install nginx -y && sudo systemctl start nginx && sudo systemctl enable nginx

- **Step 11:** Create an Nginx configuration directory:

          sudo vim /etc/nginx/sites-available/mern-app

- **Step 12:** Add the following configuration:
  {{< copyable title="ngink config" >}}
  server {
  listen 80;
  server_name cheese1512.com;

        location /api/ {
            proxy_pass http://localhost:8080/;
            proxy_http_version 1.1;
            proxy_set_header Upgrade $http_upgrade;
            proxy_set_header Connection 'upgrade';
            proxy_set_header Host $host;
            proxy_cache_bypass $http_upgrade;
        }

        location / {
            proxy_pass http://localhost:5173/;
            proxy_http_version 1.1;
            proxy_set_header Upgrade $http_upgrade;
            proxy_set_header Connection 'upgrade';
            proxy_set_header Host $host;
            proxy_cache_bypass $http_upgrade;
        }

  }
  {{< /copyable >}}

- **Step 13:**Install Certbot for SSL and enable the Nginx site:

        sudo apt install certbot python3-certbot-nginx -y
        sudo ln -s /etc/nginx/sites-available/mern-app /etc/nginx/sites-enabled/

- **Step 14:** Test & reload Nginx:

        sudo nginx -t
        sudo systemctl reload nginx

- **Step 15:** Request SSL certificate & verify DNS:

        sudo certbot --nginx -d testing.integrationsninjas.com
        nslookup testing.integrationsninjas.com

- **Step 16:** Once completed, your domain should be accessible.
- **Option 2: Using a Domain from Another Provider**

- **Step 1:** Visit [link](https://hpanel.hostinger.com)
- **Step 2:** Select **Domains → Register a new domain**
  ![Tìm kiếm domain](/images/3.Containerization/3.3/3.3.3/7.png)
- **Step 3:** Choose a domain and complete payment.
  ![Tìm kiếm domain](/images/3.Containerization/3.3/3.3.3/8.png)

- **Step 4:** After successful payment, repeat Steps 10-15 from Option 1.
- **Step 5:** Verify the results.
