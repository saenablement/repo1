pipeline {
  agent {
    node {
      label 'jdk8'
    }

  }
  stages {
    stage('say hello') {
      steps {
        echo "Hello ${MY_NAME}!"
        echo "${TEST_USER_USR} ${TEST_USER_PSW}"
        echo "Hello ${params.Name}!"
        sh 'java -version'
      }
    }
    stage('Deploy') {
      options {
        timeout(time: 30, unit: 'SECONDS')
      }
      input {
        message "Which Version?"
        ok "Deploy"
        parameters {
            choice(name: 'APP_VERSION', choices: "v1.1\nv1.2\nv1.3", description: 'What to deploy?')
        }
      }
      steps {
        echo 'Continuing with deployment'
      }
    }
  }
  environment {
    MY_NAME = 'Stefan'
    TEST_USER = credentials('test-user')
  }
  parameters {
    string(name: 'Name', defaultValue: 'whoever you are', description: 'Who should I say hi to?')
  }
}
