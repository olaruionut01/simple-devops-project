pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git branch: 'main', url:'https://github.com/olaruionut01/simple-devops-project.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
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