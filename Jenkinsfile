pipeline {
    agent any
    stages {
        stage('Clone Repo') {
            steps {
                git branch: 'main', url: 'https://github.com/Shreya-Verma2000/nginx-jenkins.git'
            }
        }

        stage('Set Minikube Docker') {
            steps {
                powershell 'minikube -p minikube docker-env --shell powershell | Invoke-Expression'
            }
        }

        stage('Build Docker Image') {
            steps {
                powershell 'cd $env:WORKSPACE; docker build -t my-nginx:1.0 .'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                powershell 'cd $env:WORKSPACE; kubectl apply -f k8s/nginx-deployment.yaml'
            }
        }
    }
}
