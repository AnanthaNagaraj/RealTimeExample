pipeline {
  agent any
  stages {
    stage('Dev-Build') {
      steps {
        git(url: 'https://github.com/AnanthaNagaraj/WebApp.git', branch: 'master', poll: true)
      }
    }

  }
}