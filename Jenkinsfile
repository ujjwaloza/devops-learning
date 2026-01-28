pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo '📥 Checking out code'
            }
        }

        stage('Build') {
            steps {
                echo '🔨 Build stage running'
            }
        }

        stage('Test') {
            steps {
                echo '🧪 Tests passed'
            }
        }
    }

    post {
        always {
            echo '🧹 Pipeline finished'
        }
    }
}
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building application'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application'
            }
        }
    }
}
