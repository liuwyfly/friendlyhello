pipeline {
    agent { docker { image 'dcdev/python:2.7-slim' } }
    environment {
        APP_NAME='gjqspecialnodelete'
    }
    stages {
        stage('get_code') {
            when{
                branch 'master'
            }
            steps {
                echo 'get code and test'
            }
        }
        stage('push_docker') {
            steps {
                echo 'push docker image'
                script {
                    def dkImage = docker.build('friendlyhello:04121814')
                    dkImage.push()
                }
            }
        }
    }
}
