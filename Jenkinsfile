pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('SIT') {
          steps {
            sh 'echo Hey SIT!'
          }
        }

        stage('UAT') {
          steps {
            sh 'echo Hello UAT!'
          }
        }

      }
    }

  }
}