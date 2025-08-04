---
title: "Create scripts to deploy React.js applications"
date: "2025-06-21"
weight: 1
chapter: false
pre: " <b> 3.2.1 </b> "
---

### Introduction

Deploying a React.js application to a production server is a complex process with multiple steps that require precise execution. Instead of performing these steps manually—which can lead to errors and wasted time—we'll create automated scripts to handle the entire process. Deployment scripts ensure consistency, minimize human error, and enable fast, reliable deployments. This is especially important when deploying multiple times or across different environments.

In a real-world production scenario, a standard React.js deployment process includes: server environment setup, dependency installation, web server configuration (Nginx), SSL setup, process management, and monitoring. Each step has its own technical details and must be executed in the correct order.

### Benefits of Scripted Deployment

- **Consistency:** Each deployment follows the exact same steps, eliminating discrepancies between deployments and ensuring a stable production environment.
- **Time Savings:** Automating repetitive tasks reduces deployment time from hours to minutes.
- **Error Reduction:** Eliminates human errors that often occur during complex manual processes.
- **Rollback Capability:** Quickly revert to a previous version if issues arise.
- **Reusability:** Scripts can be customized and reused across multiple projects and environment

### Implementation Steps

- **Step 1:** Go to **EC2 -> Instances** .

- **Step 2:** Select **instances đã tạo -> Connect -> Connect**

  ![Kết nối Instance](/images/3.Containerization/3.3/3.3.2/1.png)

- **Step 3:** Run the following command to install and configure Docker: **sudo apt-get update && sudo apt-get install docker.io -y && sudo systemctl start docker && sudo chmod 666 /var/run/docker.sock && sudo systemctl enable docker && docker --version** and then run **docker ps** to check configuration
  ![Cài đặt Docker trên Ubuntu](/images/3.Containerization/3.3/3.3.2/2.png)

- **Step 4:** Navigate to your GitHub repository **AWS-FE**, Click **Settings -> Runner -> New self-hosted runner**

  ![Truy cập Runner trong Github](/images/3.Containerization/3.3/3.3.1/1.png)

- **Step 5:** Select Runner image: **Linux** và Copy and run the provided commands on your **EC2 Instances**

  ![Truy cập Runner trong Github](/images/3.Containerization/3.3/3.3.1/2.png)

- **Step 6:** Start the runner service:

{{< copyable title="ec2" >}}
sudo ./svc.sh install
sudo ./svc.sh start

{{< /copyable >}}

- **Step 7:** Verify Runner Status, ensure the runner is active in GitHub:
  ![Truy cập Runner trong Github](/images/3.Containerization/3.3/3.3.2/5.png)
- **Step 8:** Access **Visual Studio Code** then open your project name is **AWS-FE**
- **Step 9:** Push code to GitHub. The deployment will trigger automatically under Actions.
- **Step 10:** Monitor the deployment logs for errors
  ![Truy cập Runner trong Github](/images/3.Containerization/3.3/3.3.1/3.png)
- **Step 11:** Access the application via **Public IP EC2:5173**
  ![Truy cập Runner trong Github](/images/3.Containerization/3.3/3.3.1/4.png)
