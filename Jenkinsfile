pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t node-app .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh '''
                docker stop node-container || true
                docker rm node-container || true
                '''
            }
        }

        stage('Run New Container') {
            steps {
                sh '''
                docker run -d -p 3000:3000 --name node-container node-app
                '''
            }
        }
    }
}
