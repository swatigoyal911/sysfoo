pipeline {
  agent any
  tools {
        maven 'Maven 3.8.6' 
  }
  stages{
      stage("build"){
          steps{
              echo 'Building.....'
              sh 'mvn compile'
          }
      }
      stage("test"){
          steps{
              echo 'Testing......'
              sh 'mvn clean install'
          }
      }
      stage("package"){
          steps{
              echo 'Packaging.....'
              sh 'mvn package'
              archiveArtifacts artifacts: '**/target/*.jar', followSymlinks: false
          }
      }
  }

  post{
    always{
        echo 'This pipeline is completed..'
    }
  }
}
