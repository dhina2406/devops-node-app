pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-creds')
    }

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t dhina2406/devops-node-app:latest .'
            }
        }

        stage('Docker Login') {
            steps {
                sh '''
                  echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin
                '''
            }
        }

        stage('Push to Docker Hub') {
            steps {
                sh 'docker push dhina2406/devops-node-app:latest'
            }
        }
    }
}
