pipeline {
    agent any

    stages {
        stage('Setup') {
            steps {
                echo 'Performing setup...'
            }
        }
        stage('Build') {
            steps {
                echo 'Performing build...'
            }
        }
        stage('Test') {
            steps {
                script {
                    try {
                        // Simulate test execution
                        if (Math.random() < 0.5) {
                            echo 'Test passed'
                        } else {
                            error 'Test failed'
                        }
                    } catch (Exception e) {
                        currentBuild.result = 'UNSTABLE'
                        echo "Tests failed but marking the build as unstable: ${e.message}"
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Performing deployment...'
            }
        }
    }
}

