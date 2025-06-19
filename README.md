# devops-pipeline-eks

## Jenkins CI/CD Pipeline – Microservices Deployment on AWS EKS

Hi! 👋 I’m **Mohammed Sultan**, a DevOps Engineer passionate about automation, cloud infrastructure, and microservices. This project demonstrates how I built a fully automated CI/CD pipeline using **Jenkins**, **Docker**, and **Kubernetes (EKS)** to deploy a microservices-based application on AWS.

---

## 🚀 Project Highlights

- ✅ **Automated CI/CD** from GitHub code push to EKS deployment
- 🧪 **Build & Test** Java microservices with Maven and JUnit
- 🐳 **Containerize** apps using Docker and push to **AWS ECR**
- ☸️ **Deploy** microservices to **Amazon EKS** with Helm
- 🔐 Secure credentials via Jenkins Credentials / AWS Secrets Manager
- 🔔 **Send notifications** on build/test results (Slack or Email)

---

## 🛠️ Tech Stack

| Tool             | Purpose                           |
|------------------|------------------------------------|
| **Jenkins**      | CI/CD Orchestration (Multibranch) |
| **GitHub**       | Source Code Version Control        |
| **Docker**       | Containerization                   |
| **AWS ECR**      | Docker Image Registry              |
| **AWS EKS**      | Managed Kubernetes Cluster         |
| **Helm**         | Kubernetes Deployment Automation   |
| **Maven**        | Java Build Tool                    |
| **JUnit / Newman** | Unit & Post-deployment API Tests |
| **Slack / Email**| Build Notifications                |

---

## 🔄 Jenkins Pipeline Flow

Each microservice (e.g., `user-service`, `order-service`) has a dedicated `Jenkinsfile` with the following stages:

1. **Checkout Code** from GitHub
2. **Build & Unit Test** using Maven + JUnit
3. **Docker Build** the service image
4. **Push Image** to AWS ECR
5. **Deploy** to EKS via Helm
6. **Post-Deployment API Test** using Newman

---

## 📄 Example Jenkinsfile (Simplified)

```groovy
pipeline {
  agent any
  environment {
    ECR_REPO = '1234567890.dkr.ecr.us-east-1.amazonaws.com/user-service'
  }
  stages {
    stage('Checkout') {
      steps {
        git 'https://github.com/mohammed-sultan/user-service.git'
      }
    }
    stage('Build & Test') {
      steps {
        sh 'mvn clean install'
      }
    }
    stage('Docker Build & Push') {
      steps {
        sh 'docker build -t $ECR_REPO:latest .'
        sh 'docker push $ECR_REPO:latest'
      }
    }
    stage('Deploy to EKS') {
      steps {
        sh 'helm upgrade --install user-service ./helm/user-service'
      }
    }
  }
}









🔐 Secrets Management
I use Jenkins Credentials Manager for storing secrets like AWS keys.

In production, I also use AWS Secrets Manager and fetch secrets in real-time inside the pipeline.

📁 Project Structure
sql
Copy
Edit
ci-cd-pipeline/
├── user-service/
│   ├── Jenkinsfile
│   ├── Dockerfile
│   └── helm/
├── product-service/
├── order-service/
└── shared-libs/
👨‍💻 About Me
I'm Mohammed Sultan — an aspiring DevOps & Cloud Engineer with hands-on experience in CI/CD, containerization, cloud infrastructure, and Kubernetes.

📫 Connect with me on LinkedIn


