pipeline {
  agent any
  stages {
    stage('Say Hello') {
      steps {
        echo 'Hello World!'
        echo 'Hello ${MY_NAME}!'
        echo "Hello ${MY_NAME}!"
        sh 'java -version'
      }
    }
  }
  environment {
    MY_NAME = 'Mary'
  }
}