pipeline {
    agent any

    environment {
        USER_NAME = credentials('USER_NAME')  // Store this in Jenkins → Credentials
        PORT = '5000'
    }

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/Mahendra-Cloud141/cloud-inventory-mini.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-hello .'
            }
        }

        stage('Run App in Docker') {
            steps {
                sh 'docker run -d -p 5000:5000 --env USER_NAME=$USER_NAME flask-hello'
            }
        }
    }
}
