pipeline {
  agent any
  
  stages {
    
    stage('Start') {
      steps {
        slackSend (
          channel: 'kjs-sxl4028',
          color: '#FFFF00',
          message: "STARTED"
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
}

