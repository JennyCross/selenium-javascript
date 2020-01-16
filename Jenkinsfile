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

    stage('Archive') {
      steps {
        archiveArtifacts(artifacts: '/target/site', allowEmptyArchive: true)
      }
    }

    stage('Cloud') {
      parallel {
        stage('Copy files to S3') {
          steps {
            s3Upload()
          }
        }

        stage('Copy S3 to S3') {
          steps {
            s3Copy()
          }
        }

      }
    }

    stage('Notify') {
      parallel {
        stage('Slack') {
          steps {
            slackSend()
          }
        }

        stage('Email') {
          steps {
            emailext(subject: 'selenium-javascript', body: 'Something happened!')
          }
        }

      }
    }

    stage('Chuck Norris') {
      steps {
        chuckNorris()
      }
    }

  }
  environment {
    SIT_NAME = 'Superman'
    UAT_NAME = 'Batman'
  }
}