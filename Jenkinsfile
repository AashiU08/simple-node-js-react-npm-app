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

        stage('error') {
          steps {
            emailext(subject: 'String', body: 'String', attachLog: true, to: 'aashi.upadhyay@assetvantage.com', saveOutput: true, from: 'snigdhaupadhyay08@gmail.com', mimeType: ' type=text/html exts=htm,html  type=text/plain exts=txt ', presendScript: ' this could be used to notify people that a new build is happening build.previousBuild.result.toString().equals(\'FAILURE\')', postsendScript: 'only send an email if the word {{ERROR}} is found in build logs build.logFile.text.readLines().any { it =~ /.*ERROR.*/ }')
          }
        }

      }
    }

  }
  environment {
    CI = 'true'
  }
}