pipeline{
  agent {
    docker{
      image 'maven'
      args '-v $HOME/.m2:/root/.m2'
    }
  }
  
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
          
