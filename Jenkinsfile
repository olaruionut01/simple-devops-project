pipeline {
    agent {
        docker {
            image 'python:3.12-slim'
            args '-u root:root -v /var/run/docker.sock:/var/run/docker.sock'
        }
    }

    stages {
        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/olaruionut01/simple-devops-project.git'
            }
        }
        stage('Install Dependencies') {
           
            steps {
                sh '''
                    python -m pip install --upgrade pip
                    pip install -r requirements.txt
                '''
            }
        }
        
        

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t simple-devops-app:latest .'
            }
        }
    }
}