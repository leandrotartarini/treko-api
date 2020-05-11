pipeline {
  agent {
    docker {
      image "node:8-alpine"
      args "--network=skynet"
    }
  }
  stages {
    stage("Build") {
      steps {
        echo 'http://dl-cdn.alpinelinux.org/alpine/v3.9/main' >> /etc/apk/repositories
        echo 'http://dl-cdn.alpinelinux.org/alpine/v3.9/community' >> /etc/apk/repositories
        apk update
        apk add mongodb yaml-cpp=0.6.2-r2
        mongo -version
        sh "chmod +x ./scripts/dropdb.sh"
        sh "npm install"
      }
    }
    stage("Test") {
      steps {
       sh "npm run test:ci" 
      }
    }
  }
}
