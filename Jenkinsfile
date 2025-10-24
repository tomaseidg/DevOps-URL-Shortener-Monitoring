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

        stage('Test Server') {
            steps {
                echo "Running quick smoke tests..."
                sh '''
                docker-compose up -d mariadb redis
                sleep 10  # wait for DB & Redis to be ready
                docker-compose run --rm server sh -c "npm run test || exit 1"
                '''
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
