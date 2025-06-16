pipeline{
    agent any

    stages{
        stage('code'){
            steps{
                git url: 'https://github.com/demonikkk/node-todo-cicd.git'
            }
        }
        stage('image'){
            script{
                sh "docker build -t kirmanda ."
            }
        }
        stage('container'){
            script{
                sh """
                docker kill kirmada || true
                docker rm kirmada || true
                docker run -d -p 8000:80 --name kirmada kirmanda
                """
            }
        }
    }

    post{
        success{
            echo "site deployed successfully."
        }
        failure{
            echo "site deployement failed."
        }
    }
}
