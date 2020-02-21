pipeline {
  agent {
    docker {
      image 'node:8-alpine'
      args '-p 3000:3000'
    }

  }
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            sh 'npm install'
          }
        }

        stage('email') {
          steps {
            emailext(body: 'this is the execution of the jenkins build', subject: 'Jenkins Job', to: 'aashi.upadhyay@assetvantage.com')
          }
        }

      }
    }

  }
  environment {
    CI = 'true'
  }
}