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

        stage('') {
          steps {
            emailext(subject: 'test result', body: 'this is the build result ', attachLog: true, to: 'aashi.upadhyay@assetvantage.com', saveOutput: true, from: 'snigdhaupadhyay08@gmail.com', mimeType: ' type=text/html exts=htm,html  type=text/plain exts=txt ')
          }
        }

      }
    }

  }
  environment {
    CI = 'true'
  }
}