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
    /* checkout scm */

    docker.withRegistry('https://registry.cn-hangzhou.aliyuncs.com', '922d9961-34d9-4811-bb64-3c2dd10e232e') {
        def customImage = docker.build("friendlyhello:04121816")
        customImage.push()
    }
}

