pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t nodejs-demo-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker stop node-app || true'
                sh 'docker rm node-app || true'
                sh 'docker run -d -p 3000:3000 --name node-app nodejs-demo-app'
            }
        }
    }
}
