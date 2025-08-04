---
title: "Create Dockerfile for Frontend (React.js)"
date: "2025-06-21"
weight: 2
chapter: false
pre: " <b> 3.2.2 </b> "
---

## Introduction

After setting up the development environment with Docker Desktop, Git, and other necessary tools, it's time to create a Dockerfile to containerize the React.js application. This ensures the application runs consistently across all environments, from development to production..

## Project Directory Structure

Before writing the Dockerfile, ensure your React project structure looks like this:
![Cấu trúc dự án](/images/3.Containerization/3.2/3.2.2/1.png)

1. **Create a .dockerignore File**

   First, create a **.dockerignore** file to exclude unnecessary files:
   {{< copyable title="dockerignore" >}}
   node_modules
   npm-debug.log
   build
   .dockerignore
   Dockerfile
   Dockerfile.prod
   .git
   .gitignore
   README.md
   .env
   .nyc_output
   coverage
   .cache
   .parcel-cache"

{{< /copyable >}}

2. **Dockerfile for Development Environment**
   {{< copyable title="dockerfile" >}}
   FROM node:alpine3.18 as build
   WORKDIR /app
   COPY package.json .
   RUN npm install
   COPY . .
   RUN npm run build

   FROM nginx:1.23-alpine
   WORKDIR /usr/share/nginx/html
   RUN rm -rf ./\*
   COPY --from=build /app/build .
   EXPOSE 80
   CMD ["nginx", "-g", "daemon off;"]

{{< /copyable >}}

Optimized Dockerfile for **Development**:
{{< copyable title="dockerfile" >}}

# Use Node.js Alpine for smaller image size

FROM node:18-alpine

# Install dumb-init for proper signal handling

RUN apk add --no-cache dumb-init

# Create a non-root user for security

RUN addgroup -g 1001 -S nodejs
RUN adduser -S reactjs -u 1001

# Set working directory

WORKDIR /app

# Copy package files với ownership cho user

COPY --chown=reactjs:nodejs package\*.json ./

# Switch to non-root user

USER reactjs

# Install dependencies

RUN npm ci --only=production && npm cache clean --force

# Copy source code

COPY --chown=reactjs:nodejs . .

# Expose port

EXPOSE 3000

# Use dumb-init để xử lý signals properly

ENTRYPOINT ["dumb-init", "--"]

# Start development server

CMD ["npm", "start"]

{{< /copyable >}}
