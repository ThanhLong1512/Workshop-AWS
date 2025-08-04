---
title: "Set up a CI/CD Pipeline for React.js and Nodejs with GitHub Actions"
date: "2025-06-21"
weight: 4
chapter: false
pre: " <b> 3.2.4 </b> "
---

## Introduction

CI/CD (Continuous Integration/Continuous Deployment) automates the building, testing, and deployment of applications. GitHub Actions provides a powerful platform to set up CI/CD pipelines for both Frontend (React.js) and Backend (Node.js) applications.

1.  **Frontend CI/CD Pipeline**

    Create **.github/workflows/cicd.yml** file:
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

    Create **.github/workflows/cicd.yml** file:

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
