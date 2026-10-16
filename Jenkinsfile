pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t node-cicd-app:latest .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker rm -f nodejs-cicd-container || true'
                sh 'docker run -d --name nodejs-cicd-container -p 3000:3000 node-cicd-app:latest'
            }
        }

        stage('Test Application') {
            steps {
                sh 'sleep 3'
                sh 'curl -f http://localhost:3000'
            }
        }
    }
}
