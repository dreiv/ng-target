pipeline {
    agent {
        dockerfile {
            dir: 'build'
        }
    }
    stages {
        stage('Initialize') {
            steps {
                sh 'npm install'
            }
        }
        stage('Unit Test') {
            steps {
                echo 'unit testing'
            }
        }
        stage('Convergence Testing') {
            steps {
                parallel (
                firefox: {
                    echo "Firefox Testing"
                },
                Chrome: {
                    echo "Chrome Testing"
                },
                IE: {
                    echo "IE Testing"
                },
                Mobile: {
                    echo "Mobile Testing"
                }
                )
            }
        }
        stage('Build') {
            steps {
                echo 'build'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
            }
        }
    }
}
