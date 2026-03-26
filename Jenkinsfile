pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t myapp-image:latest .'
            }
        }
        stage('Test Container') {
            steps {
                sh 'docker run -d --name test-container -p 5001:5000 myapp-image:latest'
                sh 'sleep 5 && curl http://localhost:5001'
                sh 'docker rm -f test-container'
            }
        }
    }
}
