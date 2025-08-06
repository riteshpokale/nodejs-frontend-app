pipeline {
    agent any

    environment {
        IMAGE_NAME = "ritesh-nodejs-frontend"
        CONTAINER_NAME = "nodejs-frontend-container"
    }

    stages {
        stage('Checkout') {
            steps {
                echo '📥 Checking out code from GitHub...'
                git 'https://github.com/riteshpokale/nodejs-frontend-app.git'
            }
        }

        stage('Build') {
            steps {
                echo '🔧 Building Docker image...'
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Test') {
            steps {
                echo '🧪 Running tests (placeholder)...'
                // You can replace this with actual tests if available
                sh 'echo "No tests defined. Skipping..."'
            }
        }

        stage('Deploy') {
            steps {
                echo '🚀 Deploying container...'
                sh '''
                    docker rm -f $CONTAINER_NAME || true
                    docker run -d --name $CONTAINER_NAME -p 8080:3000 $IMAGE_NAME
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline completed successfully!'
        }
        failure {
            echo '❌ Pipeline failed!'
        }
    }
}
