pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t js-cicd-app .'
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker tag js-cicd-app teejaz123/js-cicd-app'
                sh 'docker push teejaz123/js-cicd-app'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 3000:3000 js-cicd-app'
            }
        }
    }
}
