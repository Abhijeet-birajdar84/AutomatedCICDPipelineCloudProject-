pipeline {
    agent any

    environment {
        PATH = "/usr/local/bin:/usr/bin:/bin"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Abhijeet-birajdar84/AutomatedCICDPipelineCloudProject-.git'
            }
        }

        stage('Backend Test') {
            steps {
                bat '''
                cd backend
                npm install
                npm test
                '''
            }
        }

        stage('Build Docker Images') {
            steps {
                bat '''
                docker build -t backend-app ./backend
                docker build -t frontend-app ./frontend
                '''
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                bat '''
                kubectl apply -f k8s/
                '''
            }
        }
    }
}
