pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
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
                docker run -d --name my-node-app -p 2001:2001 my-node-app
                '''
            }
        }
    }
}