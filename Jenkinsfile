pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "jrrrrr/mon-app-js"
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'npm test'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t %DOCKER_IMAGE% .'
            }
        }

        stage('Push Docker Image') {
            steps {
                bat 'docker login -u jrrrrr'
                bat 'docker tag %DOCKER_IMAGE% %DOCKER_IMAGE%:latest'
                bat 'docker push %DOCKER_IMAGE%:latest'
            }
        }

    }
}