pipeline {
  agent any

  stages {

    stage("checkout") {
      steps {
        script {
          def mvnHome = tool name: 'Mavan', type: 'maven'
          checkout scm
        }
      }
    }

    stage("Build") {
      steps {
        script {
          def mvnHome = tool name: 'Mavan', type: 'maven'
          sh "${mvnHome}/bin/mvn clean compile"
        }
      }
    }

    stage("Unit Test") {
      steps {
        scrip{
          def mvnHome = tool name: 'Mavan', type: 'maven'
          sh '${mvnHome}/bin/mvn test'
        }
      }

      post {
        always {
          junit '**/target/surefire-reports/TEST-*.xml'
        }
      }
    }

  }
}
