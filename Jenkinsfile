pipeline {
    agent { docker { image 'test/jdk8:20180329-02' } }
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
            }
        }
    }
}
