pipeline {
  agent any
  stages {
    stage('preparation') {
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
    stage('configuration') {
      steps {
        echo 'running script to configure the stack'
      }
    }
  }
}