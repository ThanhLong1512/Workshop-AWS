---
title: "Create Dockerfile for Backend (Node.js/Express)"
date: "2025-06-21"
weight: 3
chapter: false
pre: " <b> 3.2.3 </b> "
---

## Introduction

After setting up the development environment with Docker Desktop, Git, and other necessary tools, and completing the Dockerfile for AWS-FE, we'll now proceed to create one for AWS-BE. This ensures our application runs consistently across all environments from development to production.

## Project Directory Structure

Before writing the Dockerfile, ensure your Node.js/Express project structure looks like this:
![Cấu trúc dự án](/images/3.Containerization/3.2/3.2.3/1.png)

1. **Create .dockerignore File**

   First, create a **.dockerignore** file to exclude unnecessary files:
   {{< copyable title="dockerignore" >}}
   node_modules
   npm-debug.log
   .git
   .gitignore
   README.md
   .env
   .env.local
   .env.development
   .env.test
   .env.production
   .nyc_output
   coverage
   .cache
   logs
   \*.log
   .DS_Store
   Dockerfile
   .dockerignore
   docker-compose.yml

{{< /copyable >}}

2. **Dockerfile for Development Environment**
   {{< copyable title="dockerfile" >}}
   FROM node:alpine3.18
   WORKDIR /app
   COPY package.json ./
   RUN npm install
   COPY . .
   EXPOSE 4000
   CMD [ "npm", "run", "start" ]

{{< /copyable >}}

Optimized Dockerfile for **Development**:
{{< copyable title="dockerfile" >}}

# Use Node.js Alpine for smaller image size

FROM node:18-alpine

# Install dumb-init để xử lý signals properly

RUN apk add --no-cache dumb-init

# Create non-root user for security

RUN addgroup -g 1001 -S nodejs
RUN adduser -S expressjs -u 1001

# Set working directory

WORKDIR /app

# Copy package files with proper ownership

COPY --chown=expressjs:nodejs package\*.json ./

# Switch to non-root user for dependency installation

USER expressjs

# Install dependencies (using npm ci for faster, reliable builds)

RUN npm ci --only=production && npm cache clean --force

# Copy source code with proper ownership

COPY --chown=expressjs:nodejs . .

# Expose backend port

EXPOSE 4000

# Use dumb-init for proper signal handling

ENTRYPOINT ["dumb-init", "--"]

# Start development server

CMD ["npm", "run", "dev"]

{{< /copyable >}}
