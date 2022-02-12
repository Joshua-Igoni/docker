pipeline {
  agent any
  stages{
    stage('Checkout') {
        steps {
            git branch: 'main', credentialsId: 'git_cred', url: 'https://git@github.com/Joshua-Igoni/docker.git'
        }
    }
    stage ("Build") {
      steps  { dir("files/python/") {
        sh "docker build -t joshbolten/pythonflashapp:latest ."
       }
      }
    }
    stage ("Deploy to Dockerhub") {
      steps {
        withCredentials([usernamePassword(credentialsId: 'docker_cred', passwordVariable: 'PASS', usernameVariable: 'USER' )]) {
          sh 'echo $PASS | $sudo docker login -u $USER --password-stdin'
          sh 'docker push joshbolten/pythonflaskapp:latest'
        }
      }  
    }
  }
}
