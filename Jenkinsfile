pipeline {
  agent any

  tools { maven 'M3' }

  stages {
    stage('Checkout') {
      steps { checkout scm }
    }

    stage('Build') {
      steps { bat 'mvn -B -DskipTests clean package' }
    }

    stage('Unit Tests') {
      steps { bat 'mvn -B test' }
      post {
        always {
         
          junit 'target/surefire-reports/*.xml'
          archiveArtifacts artifacts: 'target/**/*', fingerprint: true
        }
      }
    }
  }

  post {
    success { echo 'OK' }
    failure { echo 'FAIL' }
  }
}
