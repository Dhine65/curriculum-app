pipeline {
  agent any
  stages {
    stage('Checkout Code') {
      steps {
        git(url: 'https://github.com/Dhine65/curriculum-app', branch: 'dev')
      }
    }

    stage('Log') {
      steps {
        sh '''ls -la
'''
      }
    }

    stage('Build') {
      steps {
        sh '''sudo docker install buildx
docker buildx build -f curriculum-front/Dockerfile -t dhineshyd/curriculum-front:latest .'''
      }
    }

  }
}