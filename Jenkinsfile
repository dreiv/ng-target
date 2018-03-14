pipeline {
    try {
    agent none
    stages {
        stage('Unit Test') {
            agent {
                dockerfile {
                    additionalBuildArgs '--target test'
                }
            }
            steps {
                echo "unit test"
                // sh '$(npm bin)/ng test --browser=ChromeHeadlessCI --single-run=true'
            }
        }
        stage('Convergence Testing') {
            agent {
                dockerfile {
                    additionalBuildArgs  '--target test'
                }
            }
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
        stage('Deploy') {
            agent any
            steps {
                echo 'Deploying...'
            }
        }
    }
    } catch (err) {
        echo "miu miu"
    }
}
