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
          sh "docker build -t ${DOCKER_IMAGE}:${env.BUILD_NUMBER} ."
          sh "docker build -t ${DOCKER_IMAGE}:latest ."
        }

      }
    }

    stage('Push') {
      steps {
        script {
          docker.withRegistry('https://registry.hub.docker.com', '3e26d987-4d38-4efd-95c2-a7a7e112ce50') {
            // Push the Docker image with the build number tag
            sh "docker push ${DOCKER_IMAGE}:${env.BUILD_NUMBER}"

            // Push the Docker image with the 'latest' tag
            sh "docker push ${DOCKER_IMAGE}:latest"
          }
        }

      }
    }

  }
  environment {
    DOCKER_CREDENTIALS = 'TimZhun/release:${env.BUILD_NUMBER}'
    DOCKER_IMAGE = 'my-app'
    DOCKER_USERNAME = 'credentials(\'3e26d987-4d38-4efd-95c2-a7a7e112ce50\')'
    DOCKER_REPO = 'TimZhun/my-app'
  }
}