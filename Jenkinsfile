pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/adithep-bm/docker-jenkins-app.git'
            }
        }
        stage('Build Image') {
            steps {
                sh 'docker build -t docker-jenkins-app:latest .'
            }
        }
        stage('Run Container') {
            steps {
                sh 'docker rm -f demo-app || true'
                sh 'docker run -d -p 8081:8081 --name demo-app docker-jenkins-app:latest'
            }
        }
    }
}