pipeline {
  agent any 
  tools {
    maven 'M3'
    jdk 'jdk11'
  }
  stages {
      stage ('Build') {
        steps {
          sh 'mvn -Dmaven.test.failure.ignore=true install'
        }
      }
      stage('Sonar') {
        steps {
          script {
            def scannerHome = tool 'sonarqube'
            withSonarQubeEnv('sonarqube') {
              sh "${scannerHome}/bin/sonar-scanner"
            }
          }
        }
      }
  }
}