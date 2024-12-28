pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'echo "build"'
      }
    }

    stage('Test') {
      steps {
        sh 'echo "test"'
      }
    }

    stage('Docker') {
      steps {
        script {
          echo "tws"
        }

      }
    }

    stage('Push') {
      steps {
        sh 'docker push tamirlah/my-app:latest'
      }
    }

  }
  environment {
    DOCKER_IMAGE = 'tamirlah/my-app'
  }
}