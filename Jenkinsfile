pipeline {
  agent { label "docker" }

  environment {
    DOCKER_IMAGE = "registry.incd.ca/website-aegis"
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
        withDockerRegistry([credentialsId: 'registry-incd-ca-credentials', url: '']) {
          sh "docker push ${env.DOCKER_IMAGE}"
        }
      }
    }
    stage('Deploy') {
      steps {
        sh 'echo Not implemented'
      }
    }
  }
}
