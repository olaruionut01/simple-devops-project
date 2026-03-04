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
                docker { image 'simple-devops-app' }
            }
            steps {
                sh 'pip install --no-cache-dir -r requirements.txt'
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
                docker { image 'simple-devops-app' }
            }
            steps {
                sh 'python3 -m pytest'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t simple-devops-app .'
            }
        }
    }
}