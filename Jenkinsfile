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
        stage('Check PATH') {
            steps {
                sh 'echo $PATH'  
            }
        }

        stage('Install pytest') {
            steps {
                sh 'pip install --no-cache-dir --prefix=/tmp/pip_install pytest'
                sh '/tmp/pip_install/bin/pytest' 
            }
}

        stage('Run Tests') {
            
            steps {
                sh 'python -m pytest'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t simple-devops-app .'
            }
        }
    }
}