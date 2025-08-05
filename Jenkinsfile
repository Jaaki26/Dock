pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {
        stage('Checkout') {
            steps {
                git branch:'main', url: 'https://github.com/Jaaki26/Dock.git'
            }
        }

        stage('Build and Run Docker') {
            steps {
                sh '/usr/bin/docker-compose down || true'
                sh '/usr/bin/docker-compose up -d --build'
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
