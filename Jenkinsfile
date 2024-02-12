pipeline {
    agent any 
    environment {
    DOCKERHUB_CREDENTIALS = credentials('docker-cred')
    }
    stages { 

        stage('Build docker image') {
            steps {  
                sh 'docker build -t naveen1433/flaskapp:$BUILD_NUMBER .'
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u naveen1433 --navee123@-stdin'
            }
        }
        stage('push image') {
            steps{
                sh 'docker push naveen1433/flaskapp:$BUILD_NUMBER'
            }
        }
}
post {
        always {
            sh 'docker logout'
        }
    }
}
