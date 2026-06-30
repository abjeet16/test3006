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

    }
}
sudo chmod o+x /home/Abjeet/.kube/config
sudo chmod -R o+rx /home/Abjeet/.minikube
sudo find /home/Abjeet/.minikube -type f -exec chmod o+r {} \;