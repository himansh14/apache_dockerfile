pipeline {
  agent {
    docker {
      image 'nginx'
    }

  }
  stages {
    stage('Post Build Steps') {
      steps {
        writeFile(file: 'status.txt', text: 'Hey it worked!!!')
      }
    }

  }
}
