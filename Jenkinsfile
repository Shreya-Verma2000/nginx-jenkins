pipeline {
    agent any
    stages {
        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/Shreya-Verma2000/nginx-jenkins.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("my-nginx:1.0")
                }
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                script {
                    sh 'kubectl apply -f k8s/nginx-deployment.yaml'
                }
            }
        }
    }
}
