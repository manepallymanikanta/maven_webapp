pipeline {
  agent any
  tools {
      maven 'Maven'
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
        sh "${M2_HOME}" package"
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
