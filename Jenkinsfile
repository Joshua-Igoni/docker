pipeline {
  agent any
  stages{
    stage('Checkout') {
        steps {
            git branch: 'main', credentialsId: 'git_cred', url: 'https://git@github.com/Joshua-Igoni/docker.git'
        }
    }
    stage ("Build") {
      steps {
        sh "docker build -t joshbolten/pythonflashapp:latest ~/workspace/"automated deployment pipeline"/docker/files/python/Dockerfile"
      }
    }
    stage ("Deploy to Dockerhub") {
      steps {
        withCredentials([usernamePassword(CredentialsId: "docker_cred" , passwordVariable: "PASS", usernameVariable: "USER" )])
        sh " echo $PASS | $docker login -u $USER --password-stdin "
        sh "docker push joshbolten/pythonflaskapp:latest "
      }
    }
  }
}
