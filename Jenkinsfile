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

        stage('Build Docker Images') {
            steps {
                echo "Building Docker images..."
                sh 'docker-compose build'
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
                
                sh '''
                docker-compose up -d mariadb redis
                sleep 10  # wait for DB & Redis to start
                docker-compose run --rm server sh -c "npm run test || exit 1"
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying services..."
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
