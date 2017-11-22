pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            input 'Build?'
            echo 'Yeah!'
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
        input 'Déployer en QA?'
      }
    }
  }
}