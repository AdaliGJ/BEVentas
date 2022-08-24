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
      emailext to: 'garran191137@unis.edu.gt', 
        body: 'Build Failure on master Branch! Please review code before merging with other branches. ${currentBuild.currentResult}: Job ${env.JOB_NAME}\nMore Info can be found here: ${env.BUILD_URL}', 
        from: 'BE Ventas Manager <beventas@jenkis.com>', 
        replyTo: 'garran191137@unis.edu.gt', 
        subject: 'Build Failure',
        attachLog: true
        
    }
  }
}
