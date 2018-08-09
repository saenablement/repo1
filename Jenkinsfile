pipeline {
  agent {
    node {
      label 'jdk8'
    }

  }
  libraries {
    lib("SharedLibs")
  }
  stages {
    stage('say hello') {
      steps {
        echo 'Hello Stefan!'
        echo "${TEST_USER_USR} ${TEST_USER_PSW}"
        sh 'java -version'
      }
    }
    
    stage('Shared Lib') {
         steps {
             helloWorld("Jenkins")
         }
      }
    stage('say bye') {
      steps {
        echo 'Bye Stefan!'
      }
    }
  }
  environment {
    MY_NAME = 'Stefan'
    TEST_USER = credentials('test-user')
  }
  post {
    aborted {
      echo 'Why didn\'t you push my button?'

    }

  }
}
