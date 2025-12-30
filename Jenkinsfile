pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install & Test') {
            steps {
                script {
                    docker.image('python:3.10-slim').inside {
                        sh 'pip install -r app/requirements.txt'
                        sh 'PYTHONPATH=. pytest -q'
                    }
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
