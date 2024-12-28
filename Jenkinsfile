pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '''chmod +x ./scripts/build.sh
./scripts/build.sh'''
      }
    }

    stage('Test') {
      steps {
        sh '''chmod +x ./scripts/test.sh
./scripts/test.sh'''
      }
    }

    stage('Docker') {
      steps {
        sh 'docker build -t my-app:latest .'
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