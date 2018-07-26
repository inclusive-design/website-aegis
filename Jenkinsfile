pipeline {
  agent { label "docker" }

  environment {
    DOCKER_IMAGE = "inclusivedesign/website-aegis"
  }

  options {
    disableConcurrentBuilds()
    timeout(time: 30, unit: 'MINUTES')
  }

  stages {
    stage('Build') {
      steps {
        sh "docker build -t ${env.DOCKER_IMAGE} ."
      }
    }
    stage('Deliver') {
      steps {
        withDockerRegistry([credentialsId: 'docker-hub', url: '']) {
          sh "docker push ${env.DOCKER_IMAGE}"
        }
      }
    }
    stage('Deploy') {
      steps {
        sh 'Not implemented'
      }
    }
  }
}
