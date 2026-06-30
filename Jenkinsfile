pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Docker Build & Push') {
            steps {
                sh 'docker build -t java-demo:latest .'
            }
        }

        stage('Deploy') {
            steps {
                sh 'KUBECONFIG=/home/mca/.kube/config kubectl apply -f deployment.yaml'
                sh 'KUBECONFIG=/home/mca/.kube/config kubectl apply -f service.yaml'
                sh 'KUBECONFIG=/home/mca/.kube/config kubectl rollout restart deployment java-demo'
            }
        }
    }
}
