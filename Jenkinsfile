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
          docker.withRegistry('https://registry.hub.docker.com', 'tamirlah-docker') {
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
    DOCKER_IMAGE = 'tamirlah/my-app'
  }
}