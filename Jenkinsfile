pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            build(job: 'Build', propagate: true)
            ansiColor('xterm') {
              echo 'something that outputs ansi colored stuff'
            }
          }
        }
        stage('Code Lint') {
          steps {
            build(job: 'Sonar', propagate: true)
          }
        }
      }
    }
    stage('Unit Tests') {
      steps {
        build(job: 'Unit Tests', propagate: true)
      }
    }
    stage('Security Tests') {
      parallel {
        stage('Security Tests') {
          steps {
            build(job: 'Security-tests', propagate: true)
          }
        }
        stage('Acceptance Tests') {
          steps {
            build(job: 'Acceptance', propagate: true)
          }
        }
      }
    }
    stage('Deploy to QA') {
      environment {
        TEST = '1'
      }
      steps {
        build(job: 'Deploy', propagate: true)
      }
    }
  }
}
