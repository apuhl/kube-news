pipeline {
  agent any
  
  stages {

    stage('Build docker image') {
      steps {
        script {
          dockerapp = docker.build("apuhl/kube-news:${env.BUILD_ID}", "-f ./Dockerfile ./src")
        }
      }
    }

  }
}