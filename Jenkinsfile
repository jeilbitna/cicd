pipeline {
  agent any
  
  environment {
    SLACK_TOKEN_ID = 'slack_token'
    CHANNEL_ID = 'notification'
  }

  stages {
    
    stage('Start') {
      steps {
        slackSend (
          tokenCredentialId: "${SLACK_TOKEN_ID}",
          channel: "${CHANNEL_ID}",
          color: '#FFFF00',
          botUser: true,
          message: "STARTED - Job : ${env.JOB_NAME}, Build : ${env.BUILD_NUMBER}"
        )
      }
    }

    stage('User Check') {
      steps {
        sh 'whoami'
      }
    }

    stage('Build Directory') {
      steps {
        sh 'pwd'
      }
    }

    stage('Directory Info') {
      steps {
        sh 'ls -al'
      }
    }

    stage('Git pull') {
      steps {
        sh 'ssh root@prod "cd /var/www/html && git pull origin main"'
      }
    }
  }

  post {
    success {
      slackSend (
        tokenCredentialId: "${SLACK_TOKEN_ID}",
        channel: "${CHANNEL_ID}",
        color: '#00FF00',
        botUser: true,
        message: "성공 - ${env.JOB_NAME} #${env.BUILD_NUMBER}"
       
      )
    }
    failure {
      slackSend (
        tokenCredentialId: "${SLACK_TOKEN_ID}",
        channel: "${CHANNEL_ID}",
        color: '#00FF00',
        botUser: true,
        message: "실패 - ${env.JOB_NAME} #${env.BUILD_NUMBER} \n 상세 오류 : ${env.BUILD_URL}"
      )
    }
  }
}
