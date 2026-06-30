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
                // Adjust tagging according to your registry (e.g., Docker Hub, Nexus, or GitLab)
                sh 'docker build -t your-registry-url/java-demo:latest .'

                // Add your registry credentials in Jenkins and use them to log in and push
                sh 'docker push your-registry-url/java-demo:latest'
            }
        }

        stage('Deploy') {
            steps {
                sh 'KUBECONFIG=/home/mca/.kube/config kubectl apply -f deployment.yaml'
                sh 'KUBECONFIG=/home/mca/.kube/config kubectl apply -f service.yaml'
                // Force Kubernetes to pull the fresh image
                sh 'KUBECONFIG=/home/mca/.kube/config kubectl rollout restart deployment java-demo'
            }
        }
    }
}
