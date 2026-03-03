pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                dir('app') {
                    sh 'docker build -t devops-todo:latest .'
                }
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh '''
                minikube kubectl -- set image deployment/devops-todo-deployment \
                devops-todo=devops-todo:latest
                '''
            }
        }
    }
}
