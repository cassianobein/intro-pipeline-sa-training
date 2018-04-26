pipeline {
  agent any
  
  parameters {
    string(name: 'Name', defaultValue: 'whoever you are', description: 'Who should I say hi to?')
  }
  
  stages {
    stage('Say Hello') {
      steps {
        echo "Hello, ${params.Name}!"
        echo "${TEST_USER_USR}"
        echo "${TEST_USER_PSW}"
      }
    }
   stage('Testing') {
        failFast true
        parallel {
          stage('Java 7') {
            agent { docker 'openjdk:7-jdk-alpine' }
            steps {
              sh 'java -version'
              sleep time: 10, unit: 'SECONDS'
            }
          }
          stage('Java 8') {
            agent { docker 'openjdk:8-jdk-alpine' }
            steps {
              sh 'java -version'
              sleep time: 20, unit: 'SECONDS'
            }
          }
        }
      }
  }
  environment {
    MY_NAME = 'Mary'
    TEST_USER = credentials('test-user')
  }
  post {
    aborted {
      echo 'Why didn\'t you push my button?'
    }
  }
}
