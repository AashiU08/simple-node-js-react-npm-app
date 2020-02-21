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
            emailext(subject: 'String', body: 'String', attachLog: true, to: 'aashi.upadhyay@assetvantage.com', saveOutput: true, from: 'snigdhaupadhyay08@gmail.com', mimeType: ' type=text/html', presendScript: 'this could be used to notify people that a new build is happening build.previousBuild.result.toString().equals(\'TRUE\')')
          }
        }

      }
    }

  }
  environment {
    CI = 'true'
  }
}