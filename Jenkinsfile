node {
  stage('checkout') {
    git 'https://github.com/manepallymanikanta/maven_webapp.git'
  }
  stage('Compile-package') {
    def mvnHome = tool name: 'Mavan', type: 'maven'
    sh "${mvnHome}/bin/mvn package"
  }
}
