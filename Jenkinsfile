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

