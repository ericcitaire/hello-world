pipeline {
  agent {
    docker {
      image 'java:8-jdk'
    }
    
  }
  stages {
    stage('Initialisation') {
      steps {
        sh './gradlew'
      }
    }
  }
}