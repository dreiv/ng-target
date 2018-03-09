pipeline {
    agent {
        dockerfile {
            dir 'build'
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
                sh '$(npm bin)/ng test --browser=ChromeHeadlessCI --single-run=true'
            }
        }
        stage('Convergence Testing') {
            steps {
                parallel (
                firefox: {
                    echo "Firefox Testing"
                },
                Chrome: {
                    sh '$(npm bin)/ng e2e'
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
