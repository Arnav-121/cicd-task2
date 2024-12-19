pipeline {
    agent any
    environment {
        KUBECONFIG = credentials('kubeconfig') // Use the Jenkins credential ID
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/<your-username>/kubernetes-jenkins-pipeline.git'
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                script {
                    sh 'kubectl apply -f deployment.yaml'
                    sh 'kubectl apply -f service.yaml'
                }
            }
        }
        stage('Test Deployment') {
            steps {
                script {
                    sh 'kubectl get pods'
                    sh 'kubectl get svc'
                }
            }
        }
    }
}
