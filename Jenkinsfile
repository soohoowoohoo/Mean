pipeline {
  agent {
    docker {
      image 'node:8-alpine'
    }
    
  }
  stages {
    stage('Setup') {
      steps {
        sh '''apk --no-cache add make g++ python git
yarn install'''
      }
    }
    stage('Server Testing') {
      environment {
        MONGODB_URI = 'mongodb://jenkinstest:jenkinstest@ds051833.mlab.com:51833/mean-copy'
      }
      parallel {
        stage('Server Tests') {
          steps {
            sh 'npm run test:server'
          }
        }
        stage('Server Coverage') {
          steps {
            sh 'npm run test:coverage:server'
          }
        }
      }
    }
  }
}