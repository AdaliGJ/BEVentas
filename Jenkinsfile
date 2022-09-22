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
        body: "Build Failure en el pipline de la Branch:  ${env.BRANCH_NAME}. Por favor revise el código antes de realizar algún merge con otras ramas. Build: ${env.BUILD_DISPLAY_NAME}.", 
        from: 'BE Ventas Manager <beventas@jenkis.com>', 
        replyTo: 'garran191137@unis.edu.gt', 
        subject: "Build Failure en Job: ${env.JOB_NAME}"    
    }
  }
}
