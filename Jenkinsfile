pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t java-demo .'
            }
        }

        stage('Deploy') {
            steps {
                sh 'KUBECONFIG=/home/mca/.kube/config kubectl apply -f deployment.yaml'
                sh 'KUBECONFIG=/home/mca/.kube/config kubectl apply -f service.yaml'
            }
        }

    }
}