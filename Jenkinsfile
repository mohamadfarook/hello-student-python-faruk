pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t student-flask-app .'
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    // Stop old container if running
                    sh 'docker rm -f student-flask-container || true'

                    sh 'docker run -d -p 5000:5000 --name student-flask-container student-flask-app'
                }
            }
        }

        stage('Test App') {
            steps {
                script {
                    sh 'sleep 5'
                    sh 'curl -f http://localhost:5000'
                }
            }
        }
    }
}
