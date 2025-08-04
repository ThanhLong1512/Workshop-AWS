---
title: "Create Docker Containers"
date: "2025-06-21"
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

![Docker](/images/3.Containerization/3.2/1.png)
**Introduction to Docker and Containerization?**
Docker is a containerization platform that packages applications and their dependencies into lightweight, portable, and isolated containers. Containers run consistently across any environment.

**Why Use Docker?**

- **Consistency**: Ensures applications run identically across different environments.
- **Portability**: Easy deployment from development to production.
- **Efficiency**: More resource-efficient than virtual machines.
- **Scalability**: Effortless service scaling.

**Chuẩn bị**:

1. **Bước 1**: Verify Docker installation by copying this command to your bash terminal:
   {{< copyable >}}
   docker --version
   {{< /copyable >}}
2. **Bước 2**: If Docker isn't installed, follow this [installation guide video](https://www.youtube.com/watch?v=bw-bMhlhcpg)
3. **Bước 3**: Successful installation will display output similar to the image below:
   ![Docker](/images/3.Containerization/3.2/2.png)

### Nội dung:

- [Build and Test Containers Locally](./3.2.1-preparation//)
- [Create Dockerfile for Frontend (React.js)](./3.2.2-dockerfile-FE//)
- [Create Dockerfile for Backend (Node.js/Express)](./3.2.3-dockerfile-BE//)
- [Set up a CI/CD Pipeline for React.js and Nodejs with GitHub Actions](./3.2.4-github-action//)
