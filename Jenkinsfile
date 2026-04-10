pipeline {
    agent any

    stages {
        stage('Install') {
            steps {
                sh 'apt-get update && apt-get install -y nodejs npm'
                sh 'npm install'
            }
        }

        stage('Build Docker') {
            steps {
                sh 'docker build -t nodejs-demo-app .'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker stop node-app || true'
                sh 'docker rm node-app || true'
                sh 'docker run -d -p 3000:3000 --name node-app nodejs-demo-app'
            }
        }
    }
}
