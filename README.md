# FinalExamDevOps

## 🚀 Objective

The goal of this project is to create a Jenkins-based CI/CD pipeline hosted on an AWS EC2 instance. The pipeline automatically builds and deploys a Dockerized application **only when a merge request is accepted from the `dev` branch to the `main` branch**. It includes:

- Docker image build
- Tagging with a custom timestamp format
- Pushing image to DockerHub
- Updating `docker-compose.yaml`
- Deploying updated service on remote EC2
- Pushing config updates to GitHub `main` branch

---------

## 🔧 Tools & Technologies

- **Jenkins** (on EC2)
- **GitHub** (source control & webhook)
- **Docker & Docker Compose**
- **AWS EC2** (as build and deploy server)
- **GitHub PAT** (for pushing changes from Jenkins)
- **Shell Scripting** (inside Jenkinsfile)

---

## 🛠️ Jenkins Pipeline Flow

### ✅ Trigger Condition

- Triggered **only when a merge request is accepted** from `dev` → `main`.

> Achieved via GitHub webhook and branch filter in Jenkins multibranch pipeline or event-based trigger logic.

---

### 🔄 Pipeline Stages Overview

#### 1. **Checkout Code**

```groovy
stage('Checkout') {
    steps {
        checkout scm
    }
}
