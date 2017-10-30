pipeline {
  agent any
  stages {
    stage('Preparation') {
      steps {
        echo 'running preparation scripts'
      }
    }
    stage('Copy Environment') {
      parallel {
        stage('Copy stc-www') {
          steps {
            echo 'creating AMI for stc-www'
            echo 'launching new instances for stc-www'
          }
        }
        stage('Copy stc-batch') {
          steps {
            echo 'Creating AMI for stc-www'
            echo 'Launching EC2 instance for stc-batch'
          }
        }
        stage('Copy rds') {
          steps {
            echo 'Create RDS snapshot'
            sh 'echo "Deleting existing RDS instance"'
            echo 'Launching new RDS instance from new created snapshot from PROD'
          }
        }
      }
    }
    stage('Configuration') {
      steps {
        echo 'Cloning configuration from github enterprise'
        echo 'Running script to configure the stack'
      }
    }
    stage('Verify') {
      steps {
        input(message: 'Please confirm', id: 'confirm', ok: 'Confirm')
      }
    }
  }
}