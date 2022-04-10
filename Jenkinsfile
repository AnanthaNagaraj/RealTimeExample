pipeline {
  agent any
  stages {
    stage('Dev-Build') {
      steps {
        git(url: 'https://github.com/AnanthaNagaraj/WebApp.git', branch: 'master', poll: true)
        bat ' bat "start /min stopApp.bat"'
        bat 'bat "mvn install"'
        bat 'bat "set JENKINS_NODE_COOKIE=dontKillMe && start /min startApp.bat"'
      }
    }

    stage('UI Automation') {
      parallel {
        stage('UI Automation') {
          steps {
            git(url: 'https://github.com/AnanthaNagaraj/WebAppUiAutomation.git', branch: 'master', poll: true)
            bat 'bat \'mvn test\''
          }
        }

        stage('API-Automation') {
          steps {
            git(url: 'https://github.com/AnanthaNagaraj/WebAppApiAutomation.git', branch: 'master', poll: true)
            bat 'bat \'mvn test\''
          }
        }

      }
    }

    stage('Performance Testing') {
      steps {
        echo 'Performance Testing'
      }
    }

  }
}