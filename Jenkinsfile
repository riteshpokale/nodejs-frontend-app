pipeline {
    agent any

    environment {
        IMAGE_NAME = 'ritesh-nodejs-frontend'
        CONTAINER_NAME = 'nodejs-frontend-container'
        APP_PORT = '3000'
        HOST_PORT = '8081' // Changed from 8080 to 8081
    }

    stages {
        stage('Checkout') {
            steps {
                echo "📥 Checking out code from GitHub..."
                git 'https://github.com/riteshpokale/nodejs-frontend-app.git'
            }
        }

        stage('Build') {
            steps {
                echo "🔧 Building Docker image..."
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Test') {
            steps {
                echo "🧪 Running tests (placeholder)..."
                sh 'echo "No tests defined. Skipping..."'
            }
        }

        stage('Deploy') {
            steps {
                echo "🚀 Deploying container..."
                sh '''
                    docker rm -f $CONTAINER_NAME || true
                    docker run -d --name $CONTAINER_NAME -p $HOST_PORT:$APP_PORT $IMAGE_NAME
                '''
            }
        }
    }

    post {
        success {
            echo "✅ Deployment completed successfully!"
        }
        failure {
            echo "❌ Pipeline failed!"
        }
    }
}
