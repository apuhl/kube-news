pipeline {
  agent any
  
  stages {

    stage('Build docker image') {
      steps {
        script {
          dockerapp = docker.build("apuhl/kube-news:v${env.BUILD_ID}", "-f ./Dockerfile ./src")
        }
      }
    }

    stage('Push Docker Image') {
      steps {
        script {
          docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
            dockerapp.push("latest")
            dockerapp.push("v${env.BUILD_ID}")
          }
        }
      }
    }

    stage('Deploying Kubernetes') {
      environment {
        tag_version = "${env.BUILD_ID}"
      }

      steps {
        withKubeConfig ([credentialsId: 'kubeconfig']) {
          sh 'sed -i "s/{{TAG}}/$tag_version/g" ./manifests/deployment.yaml'
          sh 'kubectl apply -f ./manifests/deployment.yaml'
        }
      }
    }

  }
}