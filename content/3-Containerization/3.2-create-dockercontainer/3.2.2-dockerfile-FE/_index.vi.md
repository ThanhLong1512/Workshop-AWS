---
title: "Viết Dockerfile cho Frontend (React.js)"
date: "2025-06-21"
weight: 2
chapter: false
pre: " <b> 3.2.2 </b> "
---

## Giới thiệu

Sau khi đã chuẩn bị đầy đủ môi trường phát triển với Docker Desktop, Git và các công cụ cần thiết, giờ là lúc chúng ta tạo ra Dockerfile để containerize ứng dụng React.js. Việc này giúp đảm bảo ứng dụng chạy nhất quán trên mọi môi trường từ development đến production.

## Cấu trúc thư mục dự án

Trước khi viết Dockerfile, hãy đảm bảo cấu trúc dự án React của bạn như sau:
![Cấu trúc dự án](/images/3.Containerization/3.2/3.2.2/1.png)

1. **Tạo file .dockerignore**

   Đầu tiên, tạo file \*\*.dockerignore để loại trừ các file không cần thiết:
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

2. **Dockerfile cho Development Environment**
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

Dockerfile tối ưu hơn cho **development**:
{{< copyable title="dockerfile" >}}

# Sử dụng Node.js Alpine để giảm kích thước image

FROM node:18-alpine

# Install dumb-init để xử lý signals

RUN apk add --no-cache dumb-init

# Tạo user để không chạy với root

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
