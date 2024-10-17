pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'Building.....'
        sh 'mvn compile'
      }
    }

    stage('test') {
      parallel {
        stage('test') {
          steps {
            echo 'Testing......'
            sh 'mvn clean install'
          }
        }

        stage('echo') {
          steps {
            sleep 4
          }
        }

      }
    }

    stage('package') {
      steps {
        echo 'Packaging.....'
        sh 'mvn package'
        archiveArtifacts '**/target/*.jar'
      }
    }

  }
  tools {
    maven 'Maven 3.8.6'
  }
  post {
    always {
      echo 'This pipeline is completed..'
    }

  }
}