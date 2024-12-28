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
        sh '''                    docker.withRegistry(\'https://registry.hub.docker.com\', DOCKER_CREDENTIALS) {
                        // Tag the Docker image with the repository name
                        docker.image("${DOCKER_IMAGE}").tag("${DOCKER_REPO}:latest")

                        // Push the image to Docker Hub
                        docker.image("${DOCKER_REPO}:latest").push()'''
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