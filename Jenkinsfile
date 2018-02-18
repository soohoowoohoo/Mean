pipeline {
  agent {
    docker {
      image 'node:8-alpine'
    }
    
  }
  stages {
    stage('Setup') {
      agent {
        docker {
          image 'node:8-alpine'
        }
        
      }
      steps {
        sh '''apk --no-cache add make g++ python git
yarn install'''
      }
    }
    stage('Test') {
      agent {
        docker {
          image 'node:8-alpine'
        }
        
      }
      environment {
        MONGODB_URI = 'mongodb://jenkinstest:jenkinstest@ds051833.mlab.com:51833/mean-copy'
      }
      steps {
        sh 'npm run test:server'
      }
    }
  }
}