pipeline {
    agent {
        docker
    }
    stages {
        stage('Initialize') {
            agent {
                dockerfile {
                    dir 'build'
                    label 'base'
                }
            }
            steps {
                echo 'Initialize'
            }
        }
        stage('Unit Test') {
            steps {
                echo "unit test"
                // sh '$(npm bin)/ng test --browser=ChromeHeadlessCI --single-run=true'
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
                    // sh '$(npm bin)/ng e2e'
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
