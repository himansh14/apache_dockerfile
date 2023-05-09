pipeline {
  agent {
    dockerfile {
      filename 'Dockerfile'
    }

  }
  stages {
    stage('Log Tool Version') {
      parallel {
        stage('Log Tool Version') {
          steps {
            sh '''mvn --version
                  git --version
                  java -version'''
          }
        }
      }
    }
    stage('Post Build Steps') {
          steps {
            writeFile(file: 'status.txt', text: 'Hey it worked!!!')
          }
    }
   }
} 
