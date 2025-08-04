---
title: "Setting Up the Deployment Environment"
date: "2025-06-21"
weight: 1
chapter: false
pre: " <b> 3.2.1 </b> "
---

## Introduction

Before deploying the application to production, we need to prepare the necessary environment and tools. Properly setting up the environment will ensure a smooth deployment process and help avoid unexpected errors.

### What We Will Prepare

1. **Required Extensions**
2. **Containerization Tools**
3. **CI/CD Pipeline**
4. **Creating Repositories on Docker Hub**

### Steps to Implement

1. **Install Required Extensions**

- Step 1: Open Visual Studio Code and press Ctrl+Shift+X.
- Step 2: Search for Docker and click Install.
- Step 3: Repeat Step 2 for GitHub Actions.
- Step 4: Verify the installed extensions as shown below:
  ![Docker Extensions](/images/3.Containerization/3.2/3.2.1/2.png)

  2. **Containerization Tools:**

- Step 1: After successfully completing Section 3.1.1, open **Docker Desktop.**
- Step 2: Navigate as shown in the image below:
  ![Docker Desktop Guide](/images/3.Containerization/3.2/3.2.1/3.png)
- Step 3: Select **Personal access token --> Generate new token.**
  ![Docker Desktop Guide](/images/3.Containerization/3.2/3.2.1/5.png)
- Step 4: Fill in the **Docker Token Info** and click **Generate.**
  ![Docker Desktop Guide](/images/3.Containerization/3.2/3.2.1/4.png)
- Step 5: Save the two pieces of information shown below for the next steps:
  ![Docker Desktop Guide](/images/3.Containerization/3.2/3.2.1/6.png)

3. **CI/CD Pipeline:**
   - Step 1: Log in to your GitHub account.
   - Step 2: Go to your repository named **AWS-FE**
   - Step 3: Navigate to **Settings -> Secrets and variables -> Action**
   - Step 4: Click **New repository secret**
   - Step 5: Name: **DOCKER_USERNAME**, Secret: **thanhlep**
   - Step 6: Repeat for **DOCKER_PASSWORD**
     ![Docker Desktop Guide](/images/3.Containerization/3.2/3.2.1/7.png)
4. **Create Repositories on Docker Hub**

   - Step 1: Log in to your **Docker Hub Account**
   - Step 2: Select **Repositories -> Create a repository**
     ![Docker Desktop Guide](/images/3.Containerization/3.2/3.2.1/8.png)
   - Step 3: Repository name: **reactjs-web** và Visibility: **Public**
   - Step 4: Repeat the same for **nodejs-web**
     ![Docker Desktop Guide](/images/3.Containerization/3.2/3.2.1/9.png)
