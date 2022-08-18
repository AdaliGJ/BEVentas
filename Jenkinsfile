pipeline{
  agent any
  stages{
    stage("Verificación Estado"){
      steps{
        script{
          withSonarQubeEnv("sonarserver"){
            sh "mvn clean verify sonar:sonar"
          }
        }
      }
    }
  }
}
          
