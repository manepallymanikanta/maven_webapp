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
        def mvnHome = tool name: 'Mavan', type: 'maven'
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
