pipeline {
    agent any

    environment {
        IMAGE_NAME_FRONTEND = "jhgjhnh"
    }

    stages {
        stage('Clone repository') {
            steps { 
                git branch: 'main', url: 'https://github.com/Sumant3086/Docker-CI-CD-AuraFit.git'
            }
        }

        stage('Build Docker Images') {
            steps {
                script { 
                    sh 'set -e' 
                    sh 'docker build -t $IMAGE_NAME_FRONTEND -f Dockerfile .'
                }
            }
        }

        stage('Run Docker Compose') {
            steps {
                script {
                    // Clean up existing containers and start with fresh build
                    sh 'docker-compose down || true' 
                    sh 'docker-compose up -d --build'
                }
            }
        }
    }

    post {
        success {
            echo '✅ ClassAid Deployed Successfully!'
        }
        failure {
            echo '❌ Something went wrong during deployment.'
        }
    }
}