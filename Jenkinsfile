pipeline {
    agent any

    stages {
        stage('BUILD DOCKER IMAGE') {
            steps {
                echo 'Building docker image'
                sh 'docker build -t sabirsaheel0/jenkinstest:latest .'
            }
        }
        stage('BUILD LOGIN + PUSH') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'pass', usernameVariable: 'uname')]) {
                    sh 'echo ${pass} | docker login -u ${uname} --password-stdin'
                }
                sh 'docker push sabirsaheel0/jenkinstest:latest'
                sh 'docker logout'
            }
        }
    }
}
