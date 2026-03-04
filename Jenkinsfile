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
        stage('Check PATH') {
            steps {
                sh 'echo $PATH'  // Verifică calea PATH
            }
        }

        stage('Install pytest') {
            steps {
                sh 'python3 -m pip install pytest'  // Instalează pytest direct
            }
}

        stage('Run Tests') {
            agent {
                docker { image 'python:3.9-alpine' }
            }
            steps {
                sh 'export PATH=$PATH:/tmp/pip_install/bin'
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