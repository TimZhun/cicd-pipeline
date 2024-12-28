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
sh \'\'\'

docker tag my-app:latest myusername/my-app:latest

docker push myusername/my-app:latest
\'\'\''''
        }
      }

    }
    environment {
      DOCKER_CREDENTIALS = '3e26d987-4d38-4efd-95c2-a7a7e112ce50'
    }
  }