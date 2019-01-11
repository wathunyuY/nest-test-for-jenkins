pipeline {
  agent any
 
  tools {nodejs "node"}
 
  stages {
    stage('Install dependencies') {
      steps {
        dir("project"){
            sh 'ls'
            sh 'npm install'
            sh 'npm run test'
            // sh 'npm run start:dev'
        }
      }
    }
  }
  post {
        always {
            echo 'I will do this no matter what the status is'
        }
        success {
            echo 'OK'
            sh '#!/bin/sh -e\n' + "curl -X POST https://hooks.slack.com/services/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 -H \'content-type: application/json\' -d \'{\"attachments\":[{\"color\":\"good\",\"fields\":[{\"title\":\"Notes\",\"value\":\"${env.JOB_NAME} - #${env.BUILD_NUMBER} - success  \",\"short\":false}]}]}\'"
        }
        failure {
            echo 'FAIL'
            sh '#!/bin/sh -e\n' + "curl -X POST https://hooks.slack.com/services/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 -H \'content-type: application/json\' -d \'{\"attachments\":[{\"color\":\"danger\",\"fields\":[{\"title\":\"Notes\",\"value\":\"${env.JOB_NAME} - #${env.BUILD_NUMBER} - Fail  \",\"short\":false}]}]}\'"
        }
    }
}