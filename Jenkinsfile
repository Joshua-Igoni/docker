pipeline {
  agent any
  stages{
    stage ("Build") {
      steps {
        sh "cd Dockerfile/python/"
        sh "docker build -t joshbolten/pythonflaskapp:latest ."
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
