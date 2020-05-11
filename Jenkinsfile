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
        sh "apk update &&  apk --no-cache --update add openjdk11 && apk --no-cache --update add mongodb"
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
