pipeline {
  agent any
  tools {
      maven 'Maven 3.6.3'
      jdk 'jdk8'
  }

  stages {

    stage("checkout") {
      steps {
        checkout scm
      }
    }

    stage("Build") {
      steps {
        sh "${M2_HOME}" compile"
      }
    }

    stage("Unit Test") {
      steps {
        sh '${M2_HOME}" test'
      }

      post {
        always {
          junit '**/target/surefire-reports/TEST-*.xml'
        }
      }
    }

  }
}
