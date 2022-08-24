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
  }
  post {
    failure {
      mail to: 'garran191137@unis.edu.gt', 
        body: '{$BUILD_NUMBER} Build Failure on master Branch! Please review code before merging with other branches.', 
        from: 'BE Ventas Manager <beventas@jenkis.com>', 
        replyTo: 'adaligaji@gmail.com', 
        subject: 'Build Failure'
    }
  }
}
