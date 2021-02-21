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
          junit '**/target/surefire-reports/TEST-*.xml'
        }
      }
    }

    stage('Deploy WAR') {
      steps {
        sshagent(['aws-ec2']) {
          sh 'scp -o StrictHostKeyChecking=no **/target/*.war ec2-user@18.191.153.136:/opt/tomcat8/webapps/'
        }
      }
    }

  }
}
