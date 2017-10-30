pipeline {
  agent {
    node {
      label 'ec2'
    }
    
  }
  stages {
    stage('preparation') {
      steps {
        echo 'running preparation scripts'
      }
    }
    stage('copy environment') {
      steps {
        echo 'creating stc-www'
        echo 'creating stc-app'
        echo 'creating stc-batch'
      }
    }
    stage('configuration') {
      steps {
        echo 'running script to configure the stack'
      }
    }
  }
}