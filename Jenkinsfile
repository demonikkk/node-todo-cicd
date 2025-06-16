pipeline {
    agent any

    stages {
        stage('code') {
            steps {
                checkout scm
            }
        }
        stage('image') {
            steps {
                script {
                sh "docker build -t kirmanda ."
                }
            }
        }
        stage('container') {
            steps {
                script {
                sh """
                docker kill kirmada || true
                docker rm kirmada || true
                docker run -d -p 8000:80 --name kirmada kirmanda
                """
                }
            }
        }
    }

    post {
        success {
            echo "site deployed successfully."
        }
        failure {
            echo "site deployement failed."
        }
    }
}
