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
    post { 
        success { 
            sh 'docker build -t friendlyhello:04121816 .'
            sh 'docker push sudo docker push registry.cn-hangzhou.aliyuncs.com/dcdev/friendlyhello:04121816'
        }
    }
}
