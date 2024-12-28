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
        script {
          docker.withRegistry('https://registry.hub.docker.com', 'docker_hub_creds_id') {
            sh "docker push ${DOCKER_IMAGE}:${env.BUILD_NUMBER}"
            sh "docker push ${DOCKER_IMAGE}:latest"
          }
        }

      }
    }

  }
  environment {
    DOCKER_CREDENTIALS = 'TimZhun/release:${env.BUILD_NUMBER}'
    DOCKER_IMAGE = 'my-app:latest'
    DOCKER_USERNAME = 'credentials(\'3e26d987-4d38-4efd-95c2-a7a7e112ce50\')'
    DOCKER_REPO = 'TimZhun/my-app'
  }
}