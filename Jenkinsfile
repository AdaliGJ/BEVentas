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
    stage("Quality Gate") {
            steps {
              timeout(time: 5, unit: 'MINUTES') {
                waitForQualityGate abortPipeline: true
              }
            }
          }
    
  }
  post {
    failure {
      mail to: 'garran191137@unis.edu.gt', 
        body: 'Build Failure on master Branch! Please review code before merging with other branches.', 
        from: 'BE Ventas Manager <beventas@jenkis.com>', 
        replyTo: 'garran191137@unis.edu.gt', 
        subject: 'Build Failure'     
    }
  }
}
