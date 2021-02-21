pipeline {
  agent any
  tools {
      maven 'Maven'
  }

  stages {

    stage("checkout") {
      steps {
        checkout scm
      }
    }

    stage("Build") {
      steps {
        sh "${M2_HOME} clean install"
      }
    }

    stage("Unit Test") {
      steps {
        sh "${M2_HOME} test"
      }

      post {
        always {
          junit '**/target/surefire-reports/TEST-*.xml'
        }
      }
    }

  }
}
