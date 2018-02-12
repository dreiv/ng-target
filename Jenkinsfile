pipeline {
    agent {
        docker {
            image 'node:alpine' 
            args '-p 3000:3000' 
        }
    }
    environment {
        CI = 'true'
    }
    stages {
        stage('Initialize') {
            steps {
                sh 'npm install && npm update'
            }
        }
        stage('Build') { 
            steps {
                sh 'npm build' 
            }
        }
        stage('Test') {
            steps {
                sh 'ng test --single-run' 
            }
        }
    }
}
