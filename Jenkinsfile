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
        sh 'docker build -t hello_word_python .'
      }
    }

    stage('test') {
      steps {
        sh 'docker run -itd -p 8080:8080 hello_word_python'
        sleep 5
        sh 'curl localhost:8080:8080'
        sh 'docker stop hello_word_python && docker rm hello_word_python'
      }
    }

    stage('push to dockerhub') {
      steps {
        sleep 5
      }
    }

  }
}