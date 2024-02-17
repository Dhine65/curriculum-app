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
        sh '''docker build -f "curriculum-front/Dockerfile" -t dhineshyd/curriculum-front:latest .
'''
      }
    }

    stage('Log into Dockerhub') {
      environment {
        DOCKERHUB_USER = 'dhineshyd'
        DOCKERHUB_PASSWORD = 'Dhinesh@123'
      }
      steps {
        sh '''withCredentials([usernamePassword(credentialsId: \'dockerhub-credentials\', usernameVariable: \'DOCKERHUB_USER\', passwordVariable: \'DOCKERHUB_PASSWORD\')]) {
    sh \'docker login -u $DOCKERHUB_USER -p $DOCKERHUB_PASSWORD\'
}
'''
        }
      }

      stage('Push') {
        steps {
          sh 'docker push dhineshyd/curriculum-front:latest .'
        }
      }

    }
  }