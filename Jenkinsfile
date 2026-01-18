pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/Abhijeet-birajdar84/AutomatedCICDPipelineCloudProject-.git'
            }
        }

        stage('Backend Test') {
            steps {
                dir('backend') {
                    bat 'npm test'
                }
            }
        }

        stage('Build Docker Images') {
            steps {
               
                bat 'docker build -t yourdockerhub/backend ./backend'
                bat 'docker build -t yourdockerhub/frontend ./frontend'
            }
        }

        stage('Push Images') {
            steps {
                bat 'docker push yourdockerhub/backend'
                bat 'docker push yourdockerhub/frontend'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                bat 'kubectl apply -f k8s/'
            }
        }
    }
}