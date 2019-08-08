pipeline {
  agent any
  triggers {
    pollSCM('*/1 * * * *')
  }

  // delete old builds - only keep previous 5
  options {
    buildDiscarder(logRotator(numToKeepStr: '5', artifactNumToKeepStr: '5'))
  }

  stages {
    stage('Clone sources') {
      steps{
        git url: 'https://github.com/sainkuma/nodeapp.git'
      }
    }
    stage('Install') {
      steps {
        sh 'npm install'
      }
    }
    stage('Clear Install') {
      steps {
        sh 'rm -rf node_modules'
      }
    }
  }
}