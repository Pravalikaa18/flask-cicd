pipeline {
    agent any

    stages {
        stage('Clone Code') {
            steps {
                git 'https://github.com/pravalikaa18/flask-cicd.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t pravalikaa18/flask-cicd:latest .'
            }
        }

        stage('Push to Docker Hub') {
            steps {
                withDockerRegistry([credentialsId: '395ce1a5-6982-4c78-9994-4a2e8dbce27a', url: '']) {
                    sh 'docker push pravalikaa18/flask-cicd:latest'
                }
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f k8s-deployment.yaml'
            }
        }
    }
}
