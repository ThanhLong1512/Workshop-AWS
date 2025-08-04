---
title: "Deploy Scripts"
date: "2025-06-21"
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

### Overview

After completing application containerization with Docker and setting up CI/CD pipelines with GitHub Actions, the next step is to create deployment scripts to automate the process of deploying applications across different environments.

Deploy scripts are automation scripts that simplify the deployment process, from pulling Docker images, stopping/starting containers, to performing health checks and rollbacks when necessary. This becomes particularly important when you need to deploy frequently or manage multiple environments (development, staging, production)..

#### Benefits of Deploy Scripts

- **Full Automation**: Minimizes manual steps and human errors in the deployment process
- **Consistency**: Ensures deployments are executed uniformly across all environments
- **Quick Rollback**: Enables rapid reversion to previous versions when issues arise
- **Environment Management**: Handles different environment variables and configurations
- **Health Checking**: Automatically verifies application status post-deployment

#### Deploy Scripts Architecture

In this section, we'll create deployment scripts for both Frontend (React.js) and Backend (Node.js) with the following features:

- **Environment Detection**: Automatically detects and applies appropriate configurations for each environment
- **Docker Management**: Handles image pulling, container management, and resource cleanup
- **Health Monitoring**: Verifies application status after deployment
- **Logging & Notification**: Provides detailed logging and deployment result notifications
- **Rollback Mechanism**: Enables rollback to previous versions if errors occur

### Content

1.  [Creating Deployment Scripts for React.js Application](3.3.1-deploy-fe/)
2.  [Creating Deployment Scripts for Node.js Application](3.3.2-deploy-be/)
3.  [Domain & DNS Configuration with Route 53](3.3.3-domain-route53/)
