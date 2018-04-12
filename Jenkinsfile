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
    environment {
        MYDATE=sh (
            script: "date +\"%Y%m%d\"",
            returnStdout: true
        ).trim()
    }

    stage('build_push_image') {
        echo "${MYDATE}"
        docker.withRegistry('https://registry.cn-hangzhou.aliyuncs.com', '922d9961-34d9-4811-bb64-3c2dd10e232e') {
        def customImage = docker.build("dcdev/friendlyhello:04121817-${env.BUILD_ID}")
        customImage.push()
        }
    }
}

