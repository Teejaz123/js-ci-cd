pipeline {
    agent any
    environment { DOCKER_IMAGE = "js-cicd-app" }
    stages {
        stage('Checkout') { steps { checkout scm } }

        stage('Install Dependencies') {
            agent { docker { image 'node:20' } }
            steps { sh 'npm install' }
        }

        stage('Build Docker Image') {
            steps { sh "docker build -t ${DOCKER_IMAGE} ." }
        }

        stage('Run Container') {
            steps {
                sh "docker rm -f ${DOCKER_IMAGE} || true"
                sh "docker run -d -p 3000:3000 --name ${DOCKER_IMAGE} ${DOCKER_IMAGE}"
            }
        }
    }
}
