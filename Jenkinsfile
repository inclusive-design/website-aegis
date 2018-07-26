pipeline {
  agent { label "docker" }

  environment {
    DOCKER_IMAGE = '${env.JOB_NAME}'
  }

  options {
    disableConcurrentBuilds()
    timeout(time: 30, unit: 'MINUTES')
  }

  stages {
    stage('Build') {
      steps {
        sh 'docker build -t ${env.DOCKER_IMAGE}'
      }
    }
    stage('Deliver') {
      steps {
        sh 'docker push ${env.DOCKER_IMAGE}'
      }
    }
    stage('Deploy') {
      steps {
        sh 'Not implemented'
      }
    }
  }
}
