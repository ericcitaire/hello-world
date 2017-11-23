pipeline {
  agent {
    docker {
      image 'java:8-jdk'
    }
    
  }
  stages {
    stage('Build') {
      parallel {
        stage('Compilation') {
          steps {
            echo 'Compiling...'
            sleep 3
          }
        }
        stage('Static Code Analysis') {
          steps {
            echo 'Analyzing...'
            sleep 2
          }
        }
      }
    }
    stage('Deploy to QA') {
      steps {
        echo 'Deploying to QA...'
        sleep 2
      }
    }
    stage('Tests') {
      parallel {
        stage('UI Tests') {
          steps {
            echo 'Testing UI...'
            sleep 10
          }
        }
        stage('Performance Tests') {
          steps {
            echo 'Testing Performances...'
            sleep 4
          }
        }
        stage('Security Tests') {
          steps {
            echo 'Testing Security...'
            sleep 5
          }
        }
      }
    }
    stage('Deploy to Prod') {
      steps {
        echo 'Deploying to Prod...'
        sleep 8
      }
    }
  }
}