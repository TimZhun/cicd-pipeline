pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '''chmod +x test.sh
./scripts/build.sh'''
      }
    }

    stage('Test') {
      steps {
        sh '''chmod +x test.sh
./scripts/test.sh'''
      }
    }

    stage('Docker') {
      steps {
        sh 'docker build -t Dockerfile  '
      }
    }

  }
}