pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t zoya9545/novabridge-web:v2 app/'
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push zoya9545/novabridge-web:v2'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh '''
                kubectl rollout restart deployment novabridge-deployment
                '''
            }
        }
    }
}
