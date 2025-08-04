---
title: "Thiết lập CI/CD Pipeline cho React.js và Nodejs với GitHub Actions"
date: "2025-06-21"
weight: 4
chapter: false
pre: " <b> 3.2.4 </b> "
---

## Giới thiệu

CI/CD (Continuous Integration/Continuous Deployment) là quá trình tự động hóa việc build, test và deploy ứng dụng. GitHub Actions cung cấp platform mạnh mẽ để thiết lập CI/CD pipeline cho cả Frontend (React.js) và Backend (Node.js).

1.  **Frontend CI/CD Pipeline**

    Tạo file **.github/workflows/cicd.yml**
    {{< copyable title="yaml" >}}
    name: Deploy React Application

        on:

            push:
                branches:
                    - master

        jobs:

            build:
                runs-on: ubuntu-latest
                steps:
                - name: Checkout source
                uses: action/checkout@v4
                - name: Login to DockerHub
                run: docker login -u ${{ secrets.DOCKER_USERNAME }} -p ${{ secrets.DOCKER_PASSWORD }}
                - name: Build Docker image
                run: docker build -t thanhlep/reactjs-web --build-arg REACT_APP_NODE_ENV='production' --build-arg REACT_APP_SERVER_URL='${{ secrets.REACT_APP_SERVER_URL }}' .
                - name: Push Docker image
                run: docker push thanhlep/reactjs-web

            deploy:
                needs: build
                runs-on: ubuntu-latest
                steps:
                    - name: Pull image from DockerHub
                    run: docker pull thanhlep/reactjs-web:latest
                    - name: Delete old container
                    run: docker rm -f reactjs-web-container
                    - name: Run Docker container
                    run: docker run -d -p 5173:80 --name reactjs-web-container thanhlep/reactjs-web

    {{< /copyable >}}

2.  **Backend CI/CD Pipeline**

    Tạo file **.github/workflows/cicd.yml**

    {{< copyable title="yaml" >}}
    name: Deploy Node Application

    on:

        push:
             branches:
                - main

    jobs:

        build:
            runs-on: ubuntu-latest
            steps:
            - name: Checkout Source
            uses: actions/checkout@v4
            - name: Login to docker hub
            run: docker login -u ${{ secrets.DOCKER_USERNAME }} -p ${{ secrets.DOCKER_PASSWORD }}
            - name: Build Docker Image
            run: docker build -t thanhlep/nodejs-web . - name: Publish Image to docker hub
            run: docker push thanhlep/nodejs-web:latest

        deploy:

            needs: build
            runs-on: self-hosted
            steps:
                - name: Pull image from docker hub
                run: docker pull thanhlep/nodejs-web:latest
                - name: Delete old container
                run: docker rm -f nodejs-web-container
                - name: Run Docker Container
                run: docker run -d -p 4000:4000 --name nodejs-web-container -e MONGO_PASSWORD='${{ secrets.MONGO_PASSWORD }}' thanhlep/nodejs-web

    {{< /copyable >}}
