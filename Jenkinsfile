pipeline{
  
  stages{
    stage("Verificación Estado"){
      steps{
        script{
          withSonarQubeEnv("sonarserver"){
            sh "mvn sonar:sonar clean verify"
          }
        }
      }
    }
  }
}
          
