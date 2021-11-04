pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'mvn clean'
      }
    }
    stage('Test') {
      steps {
        sh 'mvn test'
      }
    }
    stage('Deploy') {
      steps {
        sh 'mvn package'
      }
    }
  }
  post {
        always {
            echo "hello from postbuild logs"
            slackSend channel: '#test',
                message: "*${currentBuild.currentResult}:* Job ${env.JOB_NAME} build ${env.BUILD_NUMBER} by ${env.BUILD_USER}\n More info at: ${env.BUILD_URL}"
        }
    }
}
