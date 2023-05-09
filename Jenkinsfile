pipeline {
  agent {
    dockerfile {
      filename 'Dockerfile'
    }

  }
  stages {
    stage('Post Build Steps') {
      parallel {
        stage('Post Build Steps') {
          steps {
            writeFile(file: 'status.txt', text: 'Hey it worked!!!')
          }
        }

        stage('Server') {
          agent {
            docker {
              image 'alpine'
            }

          }
          steps {
            sh '''echo "Building the server code..."
mvn -version
mkdir -p target
touch "target/sample.txt"'''
            stash(name: 'Server ', includes: '**/*.war')
          }
        }

        stage('Client ') {
          agent {
            docker {
              image 'tomcat'
              args '-u 0:0'
            }

          }
          steps {
            sh '''echo "Building the client code..."
npm install --save react
mkdir -p dist 
cat > dist/index.html <<EOF 
hello!
EOF 
touch "dist/client.js"'''
          }
        }

      }
    }

  }
}