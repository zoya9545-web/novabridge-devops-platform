pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Getting source code'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t novabridge-web:v2 app/'
            }
        }

        stage('Remove Old Container') {
            steps {
                sh 'docker rm -f novabridge-container || true'
            }
        }

        stage('Deploy Container') {
            steps {
                sh 'docker run -d --name novabridge-container -p 8081:80 novabridge-web:v2'
            }
        }
    }
}
