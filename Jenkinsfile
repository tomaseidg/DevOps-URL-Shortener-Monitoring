pipeline {
    agent any

    environment {
        COMPOSE_PROJECT_NAME = "kutt_app"
        // Load JWT secret from Jenkins credentials (Secret Text)
        JWT_SECRET = credentials('JWT_SECRET')
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
                sh '''
                    export JWT_SECRET=${JWT_SECRET}
                    docker-compose build server
                '''
            }
        }

        stage('Deploy Full Stack') {
            steps {
                echo "Deploying all services..."
                sh '''
                    export JWT_SECRET=${JWT_SECRET}
                    docker-compose down
                    docker-compose up -d
                '''
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
