pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  stages {
    stage('Scan') {
      steps {
        withSonarQubeEnv(installationName: 'sonarserver') { 
          sh 'chmod +x mvnw'
          sh './mvnw clean verify sonar:sonar'
        }
      }
    }
  }
}
