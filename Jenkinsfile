pipeline {
  agent {
    node {
      label 'docker'
    }

  }
  stages {
    stage('checkout') {
      steps {
        git(url: 'https://github.com/Ben-akiva/hello-world-python.git', branch: 'master')
      }
    }

    stage('build') {
      steps {
        sh 'docker build -t benakiva/hello_word_python:${BUILD_NUMBER} .'
      }
    }

    stage('test') {
      steps {
        sh 'docker run -itd -p 8080:8080 benakiva/hello_word_python:${BUILD_NUMBER}'
        sleep 5
        sh 'docker stop benakiva/hello_word_python:${BUILD_NUMBER} && docker rm benakiva/hello_word_python:${BUILD_NUMBER}'
      }
    }

    stage('push to dockerhub') {
      steps {
        sh 'docker login'
        sh 'docker puse benakiva/hello_word_python'
      }
    }

  }
}