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
      parallel {
        stage('Server Tests') {
          environment {
            MONGODB_URI = 'mongodb://jenkinstest:jenkinstest@ds051833.mlab.com:51833/mean-copy'
          }
          steps {
            sh 'npm run test:server'
          }
        }
        stage('Server Coverage') {
          environment {
            MONGODB_URI = 'mongodb://jenkinstest:jenkinstest@ds157740.mlab.com:57740/mean-copy2'
          }
          steps {
            sh 'npm run test:coverage:server'
          }
        }
      }
    }
  }
}