## Jenkins CI/CD: Master–Slave Agent Pipeline Setup 

- This repository demonstrates Jenkins Master–Slave (agent) Setup to build a Docker image and deploy it on a slave node.
- A cover song app created using Node JS is used for reference and is launchhed as a docker container.
- The application enforces a strict validation logic to ensure accuracy and consistency in judgement.
- The app is containerized with Docker, built using Jenkins, and runs on port 3000. Dockerfile is added in this repo for reference.

## Architecture

- EC2 Instance 1 → Jenkins Master
- EC2 Instance 2 → Jenkins Slave (Agent)
- DockerHub → Image registry
- Image Repo For App → https://github.com/vbaska3001/Cover-Song-App_Jenkins.git

## Features
- Jenkins master–slave architecture
- Scripted Jenkins pipeline
- Docker image build & push
- Remote deployment via Jenkins agent
- DockerHub integration
- Clean and simple CI/CD flow

## Overview

- Jenkins Server is installed on one EC2 instance (Master)
- Another Test Server - EC2 instance is configured as Jenkins Slave/Agent

<img width="600" height="400" alt="AWS EC2 Instances for Jenkins Servers" src="https://github.com/user-attachments/assets/6cb5aee6-eb4c-4117-91f4-b3db48151185" />

<img width="600" height="400" alt="Jenkins Agents Configured" src="https://github.com/user-attachments/assets/a6e38336-6a2f-4719-8f3f-58d0faa5698f" />

- Jenkins pipeline builds a Docker image on the Master Node and pushes image to DockerHub

<img width="600" height="400" alt="Jenkins Pipeline Executed Succesfully" src="https://github.com/user-attachments/assets/6da84fd6-803a-4ebb-9647-97158bbd5bfb" />

- Slave Agent pulls the image and runs the container

<img width="600" height="and 400" alt="Slave Docker Container Logs" src="https://github.com/user-attachments/assets/eabcc911-00e8-4c54-a24d-7c70307631ae" />

<img width="600" height="400" alt="NodeJS App UI" src="https://github.com/user-attachments/assets/86e90a7b-4354-491a-8e9d-0418d9073b41" />

## Setup Steps
**1️⃣ Jenkins Master (EC2 – 1)**
```
sudo apt update
```
**Install Java, Jenkins**
```
https://www.jenkins.io/doc/book/installing/linux/#:~:text=sudo%20apt%20update%0Asudo,sudo%20apt%20install%20jenkins
```
**Install Docker and Docker Compose**
```
sudo apt install -y docker.io && docker-compose
```
**Grant Docker permission:**
```
sudo chmod 777 /var/run/docker.sock
```

**Configure in Jenkins Server:**
- DockerHub credentials
- SSH credentials
- Slave agent
- Pipeline job (script added as .txt)

## 2️⃣ Jenkins Slave / Agent (EC2 – 2)
```
sudo apt update
```
**Install Java JDK**
```
sudo apt update
sudo apt install fontconfig openjdk-21-jre
java -version
```
**Install Docker**
```
sudo apt install -y docker.io && docker-compose
```
**Grant Docker permission:**
```
sudo chmod 777 /var/run/docker.sock
```
**Configure SSH key**
**Add agent credentials in Jenkins master**

## 3️⃣ Pipeline Execution

- Pipeline triggered from Jenkins master
**Master:**
- Clones repo
- Builds Docker image
- Pushes image to DockerHub

**Slave:**
- Pulls Docker image
- Runs container using Docker

## Repository Contents
- pipeline.txt – Jenkins scripted pipeline
- screenshots/ – Jenkins configuration & pipeline execution

## Outcome
- Docker image successfully built on master
- Container successfully deployed on slave agent
