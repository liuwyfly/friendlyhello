pipeline {
    agent {
        docker { 
            image 'dcdev/python:2.7-slim'
        }
    }
    environment {
        APP_NAME='gjqspecialnodelete'
    }
    stages {
        stage('list_env') {
            steps{
                echo "${env.GIT_BRANCH}"
                sh 'printenv'
            }
        }
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

node() {
    /* checkout scm */

    stage('build_push_image') {
        def MYDATE=sh (
            script: "date +\"%Y%m%d\"",
            returnStdout: true
        ).trim()

        echo "${MYDATE}"
        echo "${env.JOB_BASE_NAME}"
        echo "${env.JOB_NAME}"
        echo "${env.BRANCH_NAME}"

        docker.withRegistry('https://registry.cn-hangzhou.aliyuncs.com', '2825ee2d-9fdb-462f-9b2f-669877764af2') {
        def customImage = docker.build("dcdev/friendlyhello:${env.BRANCH_NAME}-${MYDATE}-${env.BUILD_ID}")
        customImage.push()
        }
    }
}

