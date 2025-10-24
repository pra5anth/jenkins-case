pipeline {
    environment {
        DOCKERHUB_CREDENTIALS = credentials("dhubb")
    }
    agent {
        label 'J-S2'
    }

    stages {
        stage('git') {
            steps {
                git url:'https://github.com/pra5anth/jenkins-case', branch: 'master'
            }
        }
        stage('docker') {
            steps {
                sh 'sudo docker login -u ${DOCKERHUB_CREDENTIALS_USR} -p ${DOCKERHUB_CREDENTIALS_PSW}'
                sh 'sudo docker build /home/ubuntu/jenkins/workspace/doc-t/ -t pra5anth/test'
                sh 'sudo docker push pra5anth/test'
                sh 'sudo docker pull pra5anth/test'
                sh 'sudo docker run -itd pra5anth/test -p 8180:80 --name pra5anth/test'
            }
        }
    }
}
