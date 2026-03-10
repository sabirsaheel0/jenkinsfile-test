pipeline {
    agent any

    stages {
        stage('BUILD DOCKER IMAGE') {
            steps {
                echo 'Building docker image'
                sh 'docker build -t myapp:latest .'
            }
        }
    }
}
