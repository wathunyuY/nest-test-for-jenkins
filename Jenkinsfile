pipeline {
  agent any
 
  tools {nodejs "node"}
 
  stages {
    stage('Example') {
      steps {
        git 'https://github.com/wathunyuY/nest-test-for-jenkins.git'
      }
    }
    stage('Install dependencies') {
      steps {
        dir("project"){
            sh 'ls'
            // sh 'npm install'
            // sh 'npm run test'
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
            sh '#!/bin/sh -e\n' + "curl -X POST https://hooks.slack.com/services/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 -H \'content-type: application/json\' -d \'{\"attachments\":[{\"color\":\"good\",\"fields\":[{\"title\":\"Notes\",\"value\":\"This is much easier than I thought it would be.\",\"short\":false}]}]}\'"
        }
        failure {
            echo 'FAIL'
            sh '#!/bin/sh -e\n' + "curl -X POST --data-urlencode \'{\"attachments\":[{\"color\":\"good\",\"fields\":[{\"title\":\"Notes\",\"value\":\"This is much easier than I thought it would be.\",\"short\":false}]}]}\' https://hooks.slack.com/services/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"
        }
    }
}