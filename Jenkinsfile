def mvnHome = tool name: 'Mavan', type: 'maven'

pipeline {
  agent any

  stages {

    stage("checkout") {
      steps {
        checkout scm
      }
    }

    stage("Build") {
      steps {
        sh "${mvnHome}/bin/mvn clean compile"
      }
    }

    stage("Unit Test") {
      steps {
        sh '${mvnHome}/bin/mvn test'
      }

      post {
        always {
          junit '**/target/surefire-reports/TEST-*.xml'
        }
      }
    }

  }
}
