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
        sh 'echo "docker"'
      }
    }

    stage('Push') {
      steps {
        sh '''docker.withRegistry(\'https://registry.hub.docker.com\', DOCKER_CREDENTIALS) {
docker.image("${DOCKER_IMAGE}").push()'''
        }
      }

    }
    environment {
      DOCKER_CREDENTIALS = 'TimZhun/release:${env.BUILD_NUMBER}'
    }
  }