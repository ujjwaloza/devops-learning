pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo '📥 Checking out code'
            }
        }

        stage('Node Info') {
            agent {
                docker {
                    image 'node:18-alpine'
                }
            }
            steps {
                sh 'node -v'
                sh 'npm -v'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t devops-ci-demo:latest .'
            }
        }
    }

    post {
        always {
            echo '🧹 Pipeline finished'
        }
    }
}
