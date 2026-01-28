pipeline {
    agent {
        docker {
            image 'node:18-alpine'
            args '-u root'
        }
    }

    stages {

        stage('Node Version') {
            steps {
                sh 'node -v'
                sh 'npm -v'
            }
        }
        
        stage('Build') {
            steps {
                echo 'Running build inside Docker container'
            }
        }
stage('Docker Build') {
    steps {
        sh 'docker build -t devops-ci-demo:latest .'
    }
}

    }

    post {
        success {
            echo '✅ Docker-based pipeline succeeded'
        }
        always {
            echo '🧹 Pipeline finished'
        }
    }
}

