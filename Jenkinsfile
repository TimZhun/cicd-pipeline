pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '''chmod +x /scripts/build.sh
./scripts/build.sh'''
      }
    }

    stage('Test') {
      steps {
        sh '''chmod +x /scripts/test.sh
./scripts/test.sh'''
      }
    }

    stage('Docker') {
      steps {
        sh 'docker build -t Dockerfile  '
      }
    }

    stage('Push') {
      steps {
        sh '''docker.withRegistry(\'https://registry.hub.docker.com\', \'docker_hub_creds_id\') {
    app.push("${env.BUILD_NUMBER}")
    app.push("latest")
}'''
        }
      }

    }
  }