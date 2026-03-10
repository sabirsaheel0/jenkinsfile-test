pipeline {
    agent any

    stages {
        stage('building code') {
            steps {
                echo 'Building the Node app'
            }
        }
        stage('Docker build + Docker push') {
            steps {
                script{
                    parallel(
                        "Step 1": {
                            echo "Parallel 1"
                        },
                        "Step 2": {
                            echo "Parallel 2"
                        }
                    )
                }
            }
        }
    }
}
