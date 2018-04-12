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
    }
}

node {
    checkout scm

    def customImage = docker.build("friendlyhello:04121816")
    customImage.push()
}

