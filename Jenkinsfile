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
        sh "${M2_HOME}/bin/mvn clean install"
      }
    }

    stage("Unit Test") {
      steps {
        sh "${M2_HOME}/bin/mvn test"
      }

      post {
        always {
          junit '**/multi3/target/surefire-reports/TEST-*.xml'
        }
      }
    }

  }
}
