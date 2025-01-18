pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/ize1020/minikube-project.git'
            }
        }
        stage('Prepare Deployment') {
            steps {
                sh '''
                mkdir -p output
                cp -r src/* output/
                '''
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                sh '''
                kubectl create namespace website || true
                kubectl apply -f website-deployment.yaml -n website
                '''
            }
        }
    }
}
