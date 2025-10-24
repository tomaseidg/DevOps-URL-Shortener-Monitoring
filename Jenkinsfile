pipeline {
    agent any
    environment {
        DOCKER_IMAGE = 'tomaseidg/kutt-app:${BUILD_NUMBER}'  
        DOCKER_CREDENTIALS_ID = 'dockerhub-credentials'  
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/tomaseidg/DevOps-URL-Shortener-Monitoring.git'  
            }
        }
        stage('Build and Test') {
            steps {
                script {
                    // Install Node.js dependencies and run tests (from package.json)
                    sh 'npm install'
                    sh 'npm test'  // Assumes tests exist; add if missing (e.g., Jest/Mocha)
                }
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    // Build the image using your Dockerfile (Node.js app)
                    docker.build(env.DOCKER_IMAGE)
                }
            }
        }
        stage('Push to Docker Hub') {
            steps {
                script {
                    // Authenticate and push the image
                    docker.withRegistry('https://index.docker.io/v1/', env.DOCKER_CREDENTIALS_ID) {
                        docker.image(env.DOCKER_IMAGE).push()
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    // Stop existing containers, update docker-compose.yml to use new image, and redeploy
                    sh 'docker-compose down || true'  // Gracefully stop if running
                    // Replace 'build:' with the pulled image for the 'server' service
                    sh 'sed -i "s|build:|image: ${DOCKER_IMAGE}|g" docker-compose.yml'
                    sh 'docker-compose up -d'  // Start with new image; monitoring stack (Prometheus/Grafana) persists
                }
            }
        }
    }
    post {
        always {
            sh 'docker system prune -f'  // Clean up unused images/containers
        }
        success {
            echo 'Pipeline succeeded! Kutt app deployed with monitoring.'
        }
        failure {
            echo 'Pipeline failed. Check logs for issues (e.g., tests, Docker push).'
        }
    }
}
