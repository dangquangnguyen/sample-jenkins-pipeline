pipeline {
  agent any
  stages {
    stage('Preparation') {
      agent {
        docker {
          image 'alpine:3.5'
        }
        
      }
      steps {
        echo 'running preparation scripts'
        awsIdentity()
      }
    }
    stage('Copy Environment') {
      parallel {
        stage('Copy webserver1') {
          steps {
            echo 'creating AMI for webserver1'
            echo 'launching new instances for stc-www'
            sh 'echo "Hello"'
          }
        }
        stage('Copy webserver2') {
          steps {
            echo 'Creating AMI for webserver2'
            echo 'Launching EC2 instance for webserver2'
          }
        }
        stage('Copy rds') {
          steps {
            echo 'Create RDS snapshot'
            sh 'echo "Deleting existing RDS instance"'
            echo 'Launching new RDS instance from new created snapshot from PROD'
          }
        }
        stage('Copy appserver') {
          steps {
            echo 'copying appserver instance'
          }
        }
        stage('Copy fileserver') {
          steps {
            echo 'copying file server'
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