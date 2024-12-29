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
          sh "docker build -t ${DOCKER_IMAGE}:${env.BUILD_NUMBER} -t ${DOCKER_IMAGE}:latest ."
        }

      }
    }

    stage('Push') {
      steps {
        script {
          docker.withRegistry('https://registry.hub.docker.com', 'tamirlah-docker')

          {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
          }
        }

      }
    }

  }
  environment {
    DOCKER_IMAGE = 'tamirlah/my-app'
  }
}