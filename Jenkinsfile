pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('SIT') {
          steps {
            sh 'echo Hey $SIT_NAME!'
          }
        }

        stage('UAT') {
          steps {
            sh 'echo Hello $UAT_NAME!'
          }
        }

      }
    }

    stage('Report') {
      steps {
        cucumber '**/*.json'
      }
    }

  }
  environment {
    SIT_NAME = 'Superman'
    UAT_NAME = 'Batman'
  }
}