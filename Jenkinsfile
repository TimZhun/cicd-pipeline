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
        sh '''echo "$DOCKER_USERNAME_PASSWORD" | docker login -u "$DOCKER_USERNAME" --password-stdin

                    
docker tag ${DOCKER_IMAGE} ${DOCKER_IMAGE}


docker push ${DOCKER_IMAGE}'''
      }
    }

  }
  environment {
    DOCKER_CREDENTIALS = 'TimZhun/release:${env.BUILD_NUMBER}'
    DOCKER_IMAGE = 'TimZhun/release:${env.BUILD_NUMBER}'
    DOCKER_USERNAME = 'credentials(\'3e26d987-4d38-4efd-95c2-a7a7e112ce50\')'
  }
}