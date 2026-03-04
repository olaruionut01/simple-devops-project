pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/olaruionut01/simple-devops-project.git'
            }
        }
        stage('Install Dependencies') {
            agent {
                docker { image 'python:3.9-alpine' }
            }
            steps {
                sh 'pip install --prefix=/tmp/pip_install -r requirements.txt'
            }
        }
        stage('Run Tests') {
            agent {
                docker { image 'python:3.9-alpine' }
            }
            steps {
                sh 'pytest'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t simple-devops-app .'
            }
        }
    }
}