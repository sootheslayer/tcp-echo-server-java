pipeline {
  agent any
  
  tools {
    jdk 'openjdk-16'
    maven 'maven3'
    dockerTool 'docker'
  }


  stages {
    stage('Git Clone') {
      steps {
        git changelog: false, poll: false, url: 'https://github.com/sootheslayer/tcp-echo-server-java.git'
      }
    }
    
    stage('Build') {
      steps {
        sh "mvn clean package"
      }
    }


    stage('Deploy') {
      steps {
        docker.build("ultimatedockerfarm/echo-server:$BUILD_NUMBER").push()
      }
    }
  }
}
