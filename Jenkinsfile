pipeline {
  agent {
    docker {
      image 'node:8-alpine'
    }
    
  }
  stages {
    stage('Setup') {
      steps {
        sh '''pwd
export PATH=$PATH:~/.yarn/bin
yarn install'''
      }
    }
    stage('Test') {
      steps {
        sh 'export MONGODB_URI=\'mongodb://jenkinstest:jenkinstest@ds051833.mlab.com:51833/mean-copy\' && npm run test:server'
      }
    }
  }
}