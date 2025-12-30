pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "sample-devops-app"
    }

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/MaheshrajV/jenkins-docker-pipeline-mastery.git'
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
                    sh "docker build -t ${DOCKER_IMAGE}:latest ."
                }
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker rm -f app || true'
                sh "docker run -d --name app -p 5000:5000 ${DOCKER_IMAGE}:latest"
            }
        }
    }

    post {
        success {
            echo "Build Passed!"
        }
        failure {
            echo "Build Failed!"
        }
    }
}
