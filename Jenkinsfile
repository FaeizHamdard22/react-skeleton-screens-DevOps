pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', url: 'https://github.com/FaeizHamdard22/react-skeleton-screens-DevOps.git'
      }
    }

    stage('Build Docker Image') {
      steps {
        script {
          dockerImage = docker.build("react-skeleton-app")
        }
      }
    }

    stage('Run Docker Container') {
      steps {
        script {
          sh "docker run -d -p 8080:80 --name react-skeleton-app react-skeleton-app || true"
        }
      }
    }
  }
}

