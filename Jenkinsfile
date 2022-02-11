pipeline {
  agent any
  stages{
    stage ("Build") {
      steps {
<<<<<<< HEAD
        sh "docker build -t joshbolten/pythonflaskapp:latest /Dockerfile/python/Dockerfile"
=======
        sh "docker build -t joshbolten/pythonflaskapp:latest ./Dockerfile/python/Dockerfile"
>>>>>>> 791e28e764b2274dc1ba6cb3db83746136beddc3
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
