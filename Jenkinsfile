pipeline {
  
  agent any
  
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhub-cred-mvmelo57')
  }
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t mvmelo57/dp-alpine-branch1:latest .'
      }
    }
    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('Push') {
      steps {
        sh 'docker push mvmelo57/dp-alpine-branch1:latest'
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}
