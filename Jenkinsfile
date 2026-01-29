pipeline {
    agent any

    environment {
        IMAGE_NAME = "ujjwaloza/devops-ci-demo"
        IMAGE_TAG  = "1.0.${BUILD_NUMBER}"
    }

    stages {
        stage('Checkout') { steps { echo 'Checkout' } }

        stage('Node Info') {
            agent { docker { image 'node:18-alpine' } }
            steps {
                sh 'node -v'
                sh 'npm -v'
            }
        }

        stage('Docker Build') {
            steps {
                sh "docker build -t ${IMAGE_NAME}:${IMAGE_TAG} -t ${IMAGE_NAME}:latest ."
            }
        }

        stage('Docker Login') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-creds',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASS'
                )]) {
                    sh 'echo "$DOCKER_PASS" | docker login -u "$DOCKER_USER" --password-stdin'
                }
            }
        }

        stage('Docker Push') {
            steps {
                sh "docker push ${IMAGE_NAME}:${IMAGE_TAG}"
                sh "docker push ${IMAGE_NAME}:latest"
            }
        }

        stage('Deploy with Docker Compose') {
    steps {
        sh '''
        docker rm -f devops_app || true
        docker-compose pull
        docker-compose up -d
        '''
    }
}
	stage('Verify Deployment') {
    steps {
        sh '''
        echo "⏳ Waiting for container to start..."
        sleep 5

        echo "🔍 Checking container status..."
        docker ps | grep devops_app

        echo "✅ Deployment verified"
        '''
    }
}
	stage('Cleanup') {
    steps {
        sh 'docker image prune -f'
    }
}


    }

    stage('Verify Deployment') {
    steps {
        sh '''
        echo "⏳ Waiting for container to start..."
        sleep 5

        echo "🔍 Checking container status..."
        docker ps | grep devops_app

        echo "✅ Deployment verified"
        '''
    }
}

}
