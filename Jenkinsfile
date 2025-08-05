pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Jaaki26/Dock.git'
            }
        }

        stage('Build and Run Docker') {
            steps {
                sh 'docker-compose down || true'
                sh 'docker-compose up -d --build'
            }
        }
    }

    post {
        success {
            echo '✅ App Deployed Successfully'
        }
        failure {
            echo '❌ Build Failed!'
        }
    }
}
