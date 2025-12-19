🚀 End-to-End DevOps Pipeline for Node.js Application
📌 Project Overview

This project demonstrates an end-to-end DevOps CI/CD pipeline for a simple Node.js application. The application is containerized using Docker, integrated with Jenkins for Continuous Integration, stored in Docker Hub, and deployed on an AWS EC2 instance. Basic infrastructure and application monitoring were implemented using Prometheus and Node Exporter.

The goal of this project is to showcase real-world DevOps workflows, automation concepts, and cloud deployment practices.

🧩 Architecture Overview

Flow:

Developer → GitHub → Jenkins (CI/CD) → Docker Hub → AWS EC2 (App Server)
                                              ↓
                                       Prometheus + Node Exporter
🛠️ Tools & Technologies Used
Category	Tools
Version Control	Git, GitHub
CI/CD	Jenkins
Containerization	Docker
Cloud Platform	AWS EC2
Monitoring	Prometheus, Node Exporter
Programming Language	Node.js
Operating System	Ubuntu Linux

📂 Project Structure
devops-node-app/
├── app.js
├── package.json
├── Dockerfile
├── Jenkinsfile
└── README.md

🔹 Phase 1: Application Development

A simple Node.js web application

Exposes port 3000

Displays the message:

Hello from DevOps Pipeline

🔹 Phase 2: Dockerization

The application is containerized using Docker.

Dockerfile
FROM node:18
WORKDIR /app
COPY . .
RUN npm install
EXPOSE 3000
CMD ["node", "app.js"]

Docker Commands
docker build -t dhina2406/devops-node-app:latest .
docker push dhina2406/devops-node-app:latest


The Docker image is stored in Docker Hub.

🔹 Phase 3: CI/CD Pipeline with Jenkins

Jenkins is installed on an AWS EC2 instance and configured to automate the build and push process.

Jenkins Pipeline Stages

Checkout Source Code from GitHub

Build Docker Image

Login to Docker Hub

Push Image to Docker Hub

Jenkinsfile (High Level)
pipeline {
    agent any
    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t dhina2406/devops-node-app:latest .'
            }
        }
        stage('Docker Login') {
            steps {
                sh 'docker login -u $DOCKER_USER -p $DOCKER_PASS'
            }
        }
        stage('Push Image') {
            steps {
                sh 'docker push dhina2406/devops-node-app:latest'
            }
        }
    }
}

🔹 Phase 4: Deployment on AWS EC2

Docker installed on Application EC2

Image pulled from Docker Hub

Application exposed via EC2 public IP

Deployment Commands
docker pull dhina2406/devops-node-app:latest
docker run -d -p 80:3000 dhina2406/devops-node-app:latest


Application accessible via:

http://<EC2-PUBLIC-IP>

🔹 Phase 5: Monitoring (Prometheus & Node Exporter)
Node Exporter

Installed on EC2

Metrics exposed at:

http://<EC2-IP>:9100/metrics

Prometheus

Configured to scrape Node Exporter metrics

Metrics verified through Prometheus UI

Although Grafana dashboards were not fully finalized, metrics collection was successfully validated using Prometheus and Node Exporter.

⚠️ Challenges Faced & Solutions
Challenge	Resolution
Docker daemon errors on Windows	Restarted Docker Desktop
Jenkins Git branch mismatch	Aligned pipeline with main branch
Dockerfile not found in Jenkins	Fixed project directory structure
Prometheus metrics not visible initially	Verified Node Exporter /metrics endpoint
🚀 Future Enhancements

Add Grafana dashboards

Automate deployment via Jenkins

Use Terraform for infrastructure provisioning

Deploy application using Kubernetes

Implement security scanning in pipeline

🎯 Key Learnings

End-to-end CI/CD pipeline design

Docker image lifecycle management

Jenkins automation and credentials handling

AWS EC2 deployment practices

Monitoring using Prometheus

🧑‍💻 Author

Dhina
Aspiring DevOps / Cloud Engineer
GitHub: https://github.com/dhina2406

✅ Conclusion

This project demonstrates practical DevOps skills including CI/CD automation, containerization, cloud deployment, and monitoring. It reflects real-world scenarios and common troubleshooting tasks faced by DevOps engineers.

