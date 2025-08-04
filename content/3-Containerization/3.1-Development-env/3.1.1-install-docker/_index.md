---
title: "Install Docker Desktop"
date: "2025-06-21"
weight: 1
chapter: false
pre: " <b> 3.1.1 </b> "
---

### Overview of Docker

![Docker](/images/3.Containerization/3.1/3.1.1/1.png)

**Docker** is a platform for developers and sysadmins to develop, deploy, and run applications using containers. It allows the creation of isolated and independent environments to launch and develop applications, and these environments are called containers. When you need to deploy to any server, simply run the Docker container, and your application will launch immediately.

**Key Components of Docker**

![Docker](/images/3.Containerization/3.1/3.1.1/2.png)

**How Docker Works**

![Docker](/images/3.Containerization/3.1/3.1.1/3.png)

1.  What is **Containerization**?

    **Containerization** is a virtualization technology that solves this problem by packaging an application and all its dependencies (such as libraries and configurations) into an independent unit called a container. This container ensures that the software runs stably and consistently in any environment, whether on a developer's personal computer, a test server, or a production environment in the cloud.

    - Before containers: A developer writes an application on their personal computer using Python version 3.6. After successful testing, they deploy the application to a production server, but this server is running Python version 3.7. This minor difference causes errors because some libraries are incompatible with Python 3.7.

    - With containers: The developer can package their application along with all the required libraries, including Python 3.6, into a container. When this container is deployed in any environment (local, test, production), the application will run exactly as it did during testing on the personal computer.

2.  The Role of **Containerization**

- **Consistency**: Ensures that the application packaged in a container behaves the same way in every environment, whether on a developer's machine, a test server, or a production environment.

- **Portability**: Containers are lightweight software packages that can be easily moved from one system to another without compatibility issues.

- **Scalability**: Containers can be quickly started or stopped, allowing applications to scale up or down based on actual demand.

- **Efficiency**: Containers share the host operating system's kernel, unlike traditional virtual machines that require a full operating system. This makes containers more resource-efficient, faster to start, and easier to manage.

- **Isolation**: Containers ensure that applications are isolated from each other, enhancing security. If one application is compromised, the issue does not affect other applications.

### Guide to Installing and Using Docker

{{%notice warning%}}
This guide is only for **Windows** operating systems.

- If you are using macOS or another operating system, please look for the appropriate documentation, as installation steps and system requirements may differ significantly.

- Verify your operating system before proceeding to avoid errors or incompatible installations.
  {{%/notice%}}

1. Download the Docker Desktop application from this [link](https://docs.docker.com/desktop/setup/install/windows-install/), Note: If your computer uses an ARM chip, download the version below. If you use Intel or AMD x86/x64 chips, download the version above.

![Docker](/images/3.Containerization/3.1/3.1.1/4.png)

2. Double-click the **Docker Desktop Installer.exe** file downloaded in step 1 to begin installation. By default, **Docker Desktop** is installed at C:\Program Files\Docker\Docker. Then click **OK** to proceed.

![Docker](/images/3.Containerization/3.1/3.1.1/85.png)

3. After installation is complete, click **Close and Restart**.
4. Open CMD and type **wsl**. If the output resembles the image below, you have succeeded.

![Docker](/images/3.Containerization/3.1/3.1.1/6.png)
