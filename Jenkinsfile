pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'master', url: 'https://github.com/shalwin04/sample-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("sample-app")
                }
            }
        }

        stage('Deploy in Docker') {
            steps {
                script {
                    sh "docker rm -f sample-app || true"
                    dockerImage.run("-d -p 8081:80 --name sample-app")
                }
            }
        }
    }
}

