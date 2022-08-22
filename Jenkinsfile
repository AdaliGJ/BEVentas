pipeline{
  agent any
  stages{
    stage("Verificación Estado"){
      steps{
        script{
          withSonarQubeEnv("sonarserver"){
            sh './mvnw clean org.sonarsource.scanner.maven:sonar-maven-plugin:3.9.0.2155:sonar'
          }
        }
      }
    }
  }
}
          
