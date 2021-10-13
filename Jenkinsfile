pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat 'mvn clean'
      }
    }
    stage('Test') {
      steps {
        bat 'mvn test'
      }
    }
    stage('Deploy') {
      steps {
        bat 'mvn package'
      }
    }
    stage('report') {
      steps {
        cucumber fileIncludePattern: '**/*.json', sortingMethod: 'ALPHABETICAL'
      }
    }
  }
}
