pipeline {
    agent any
    environment {
        REPO_URL = 'https://github.com/mohsin5450/Automated-CI-CD-Pipeline.git'
        DOCKER_IMAGE_NAME = 'web-app:latest'
    }
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: REPO_URL
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Build') {
            steps {
                echo 'No build step needed for pure JavaScript'
            }
        }
        stage('Test') {
            steps {
                sh 'npm test'
            }
        }
        stage('Docker Build') {
            steps {
                script {
                    docker.build(DOCKER_IMAGE_NAME)
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                   docker.image(DOCKER_IMAGE_NAME).run('-d -p 8000:8000 --name web-app:latest')
                }
            }
        }
    }
}

