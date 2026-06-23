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
                sh 'docker build -t my-node-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop my-node-app || true
                docker rm my-node-app || true
                docker run -d --name my-node-app -p 2001:3000 my-node-app
                '''
            }
        }
    }
}