pipeline {
    agent any

    stages {
        stage('BUILD DOCKER IMAGE') {
            steps {
                echo 'Building docker image'
                sh 'docker build -t sabirsaheel0/jenkinstest:${BUILD_NUMBER} .'
            }
        }
        stage('BUILD LOGIN + PUSH') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'pass', usernameVariable: 'uname')]) {
                    sh 'echo ${pass} | docker login -u ${uname} --password-stdin'
                }
                sh 'docker push sabirsaheel0/jenkinstest:${BUILD_NUMBER}'
                sh 'docker logout'
            }
        }
        stage('Clean Images'){
            steps{
                sh 'docker rmi sabirsaheel0/jenkinstest:${BUILD_NUMBER}'
            }
        }
    }
    post {
        success {
            echo "Pipeline is successful"
            slackSend channel: "jenkins-notifications",color: 'good', tokenCredentialId: 'slack', message: "my-first-pipeline-slack passed successfully"
        }
        failure {
            echo "Pipeline failed"
            slackSend channel: "jenkins-notifications",color: 'bad', tokenCredentialId: 'slack', message: "my-first-pipeline-slack did not pass"
        }
    }
}
