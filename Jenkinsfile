pipeline {
    agent any

    environment {
        COMPOSE_PROJECT_NAME = "kutt_app"
    }

    stages {
        stage('Checkout') {
            steps {
                echo "Checking out the code..."
                checkout scm
            }
        }

        stage('Build Server Only') {
            steps {
                echo "Building server Docker image using cache..."
                sh 'docker-compose build server'
            }
        }

        stage('Deploy Full Stack') {
            steps {
                echo "Deploying all services..."
                sh 'docker-compose up -d'
            }
        }
    }

    post {
        success {
            echo 'Pipeline succeeded! ✅'
        }
        failure {
            echo 'Pipeline failed! ❌'
        }
    }
}

