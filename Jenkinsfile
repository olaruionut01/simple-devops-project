pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/olaruionut01/simple-devops-project.git'
            }
        }
        stage('Install Dependencies') {
           
            steps {
                sh 'pip install "--prefix=/tmp/pip_install" -r requirements.txt'
            }
        }
        
        

      

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t simple-devops-app .'
            }
        }
    }
}