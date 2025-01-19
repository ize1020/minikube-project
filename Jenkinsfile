pipeline {
    agent {
        kubernetes {
            label 'jenkins-agent'
            yaml """
            apiVersion: v1
            kind: Pod
            spec:
              containers:
              - name: jnlp
                image: jenkins/inbound-agent:latest
              - name: kubectl
                image: bitnami/kubectl:latest
                command:
                - cat
                tty: true
            """
        }
    }
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/ize1020/minikube-project.git'
            }
        }
        stage('Prepare Deployment') {
            steps {
                container('jnlp') {
                    sh '''
                    mkdir -p output
                    cp -r src/* output/
                    '''
                }
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                container('kubectl') {
                    sh '''
                    kubectl create namespace website || true
                    kubectl apply -f website-deployment.yaml -n website
                    '''
                }
            }
        }
    }
}
