pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/dhina2406/devops-node-app'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t dhina2406/devops-node-app:latest .'
            }
        }

        stage('Push to Docker Hub') {
            steps {
                sh 'docker push dhina2406/devops-node-app:latest'
            }
        }
    }
}
