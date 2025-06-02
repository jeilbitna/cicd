pipeline {
  agent any
  
  stages {
    stage('User Check') {
      steps {
        whoami
      }
    }

    stage('Build Directory') {
      steps {
        pwd
      }
    }

    stage('Directory Info') {
      steps {
        ls -al
      }
    }

    stage('Git pull') {
      steps {
        ssh root@prod "cd /var/www/html && git pull origin main"
      }
    }
  }
}
