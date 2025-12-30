pipeline {
    agent {
        docker { image 'python:3.10-slim' }
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                dir('app') {
                    sh 'pip install -r requirements.txt'
                }
            }
        }

        stage('Run Tests') {
            steps {
                dir('app') {
                    sh 'pytest -q'
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                dir('app') {
                    sh 'docker build -t sample-devops-app:latest .'
                }
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker rm -f app || true'
                sh 'docker run -d --name app -p 5000:5000 sample-devops-app:latest'
            }
        }
    }
}
