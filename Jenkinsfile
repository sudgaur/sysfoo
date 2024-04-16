pipeline {
  agent any
  stages {
    stage('build') {
      parallel {
        stage('build') {
          steps {
            echo 'compiling the code...'
            sh 'mvn compile'
          }
        }

        stage('') {
          steps {
            sleep 5
          }
        }

      }
    }

    stage('test') {
      parallel {
        stage('test') {
          steps {
            echo 'running unit tests...'
            sh 'mvn clean test'
          }
        }

        stage('') {
          steps {
            sleep 5
          }
        }

      }
    }

    stage('package') {
      parallel {
        stage('package') {
          steps {
            echo 'generating artifacts...'
            sh 'mvn package -DskipTests'
            archiveArtifacts 'target/*.war'
          }
        }

        stage('') {
          steps {
            sleep 5
          }
        }

      }
    }

  }
  tools {
    maven 'Maven 3.6.3'
  }
  post {
    always {
      echo 'This pipeline is completed..'
    }

  }
}