pipeline {
  agent any
  environment {
    BUILD_USER = ''
  }
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
            script {
                BUILD_USER = getBuildUser()
            }
            echo "hello from postbuild logs"
            slackSend channel: '#test',
                color: COLOR_MAP[currentBuild.currentResult],
                message: "*${currentBuild.currentResult}:* Job ${env.JOB_NAME} build ${env.BUILD_NUMBER} by ${BUILD_USER}\n More info at: ${env.BUILD_URL}"
        }
    }
}
