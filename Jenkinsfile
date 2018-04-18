pipeline {
    agent {
        docker { 
            image 'dcdev/python:2.7-slim'
            label 'a05'
        }
    }
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

node('a05') {
    /* checkout scm */

    stage('build_push_image') {
        def MYDATE=sh (
            script: "date +\"%Y%m%d\"",
            returnStdout: true
        ).trim()

        echo "${MYDATE}"
        docker.withRegistry('https://registry.cn-hangzhou.aliyuncs.com', '2825ee2d-9fdb-462f-9b2f-669877764af2') {
        def customImage = docker.build("dcdev/friendlyhello:${MYDATE}-${env.BUILD_ID}")
        customImage.push()
        }
    }
}

