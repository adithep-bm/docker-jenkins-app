pipeline {
    agent {
        docker {
            image 'docker:20.10.7'
            args '-v /var/run/docker.sock:/var/run/docker.sock'
        }
    }
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
                sh 'docker run -d -p 5000:5000 --name demo-app docker-jenkins-app:latest'
            }
        }
    }
}
