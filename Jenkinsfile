pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  stages {
    stage('SonarQube Scan') {
      steps {
        withSonarQubeEnv(installationName: 'sonarserver') { 
          sh 'chmod +x mvnw'
          sh './mvnw clean verify sonar:sonar'
        }
      }
    }
    stage('send email'){
      steps {
        mail bcc: '', body: 'The build of this project failed!', cc: '', from: 'BE Ventas Manager <beventas@jenkis.com>', replyTo: 'adaligaji@gmail.com', subject: 'Build Failure', to: 'garran191137@unis.edu.gt'
      }
    }
  }
}
