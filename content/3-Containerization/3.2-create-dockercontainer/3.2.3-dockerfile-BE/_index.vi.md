---
title: "Viết Dockerfile cho Backend (Node.js/Express)"
date: "2025-06-21"
weight: 3
chapter: false
pre: " <b> 3.2.3 </b> "
---

## Giới thiệu

Sau khi đã chuẩn bị đầy đủ môi trường phát triển với Docker Desktop, Git và các công cụ cần thiết và đã sau khi hoàn tất việc tạo dockerfile cho **AWS-FE** tiếp tục ta sẽ thực hiện cho **AWS-BE**. Việc này giúp đảm bảo ứng dụng chạy nhất quán trên mọi môi trường từ development đến production.

## Cấu trúc thư mục dự án

Trước khi viết Dockerfile, hãy đảm bảo cấu trúc dự án React của bạn như sau:
![Cấu trúc dự án](/images/3.Containerization/3.2/3.2.3/1.png)

1. **Tạo file .dockerignore**

   Đầu tiên, tạo file \*\*.dockerignore để loại trừ các file không cần thiết:
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

2. **Dockerfile cho Development Environment**
   {{< copyable title="dockerfile" >}}
   FROM node:alpine3.18
   WORKDIR /app
   COPY package.json ./
   RUN npm install
   COPY . .
   EXPOSE 4000
   CMD [ "npm", "run", "start" ]

{{< /copyable >}}

Dockerfile tối ưu hơn cho **development**:
{{< copyable title="dockerfile" >}}

# Sử dụng Node.js Alpine để giảm kích thước image

FROM node:18-alpine

# Install dumb-init để xử lý signals properly

RUN apk add --no-cache dumb-init

# Tạo user để không chạy với root privileges

RUN addgroup -g 1001 -S nodejs
RUN adduser -S expressjs -u 1001

# Set working directory

WORKDIR /app

# Copy package files với ownership cho user

COPY --chown=expressjs:nodejs package\*.json ./

# Switch to non-root user để install dependencies

USER expressjs

# Install dependencies (sử dụng npm ci cho faster, reliable builds)

RUN npm ci --only=production && npm cache clean --force

# Copy source code với proper ownership

COPY --chown=expressjs:nodejs . .

# Expose port mà backend sẽ chạy

EXPOSE 4000

# Use dumb-init để xử lý signals properly

ENTRYPOINT ["dumb-init", "--"]

# Start development server

CMD ["npm", "run", "dev"]

{{< /copyable >}}
