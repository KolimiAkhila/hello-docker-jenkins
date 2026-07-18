pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/KolimiAkhila/hello-docker-jenkins.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''whoami
                docker build -t hello-app .'''
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop hello-app || true
                docker rm hello-app || true
                docker run -d \
                --name hello-app \
                -p 5000:8080 \
                hello-app
                '''
            }
        }
    }
}