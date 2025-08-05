pipeline {
    agent any

    environment {
        IMAGE_NAME = "riteshpokale/nodejs-frontend-app"
        CONTAINER_NAME = "nodejs-app"
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/riteshpokale/nodejs-frontend-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Stop Previous Container') {
            steps {
                sh '''
                    if [ $(docker ps -q -f name=$CONTAINER_NAME) ]; then
                        docker stop $CONTAINER_NAME
                        docker rm $CONTAINER_NAME
                    fi
                '''
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 8080:3000 --name $CONTAINER_NAME $IMAGE_NAME'
            }
        }
    }

    post {
        always {
            echo "Pipeline execution completed!"
        }
    }
}
