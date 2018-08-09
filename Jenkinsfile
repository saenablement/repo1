pipeline {
  agent {
    node {
      label 'jdk8'
    }

  }
  stages {
    stage('say hello') {
      steps {
        echo 'Hello Stefan!'
        echo "${TEST_USER_USR} ${TEST_USER_PSW}"
        sh 'java -version'
      }
    }
    stage('Testing') {
        parallel {
          stage('Java 8') {
            agent { label 'jdk9' }
            steps {
              container('maven8') {
                sh 'mvn -v'
              }
            }
          }
          stage('Java 9') {
            agent { label 'jdk8' }
            steps {
              container('maven9') {
                sh 'mvn -v'
              }
            }
          }
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
