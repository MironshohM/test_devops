pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build Image') {
            steps {
                sh 'docker build -t spring-app:latest .'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker stop spring-app || true'
                sh 'docker rm spring-app || true'
                sh 'docker run -d --name spring-app -p 8080:8080 spring-app:latest'
            }
        }
    }
}