pipeline {
  agent any

  stages {
    stage('Build & Test in Docker') {
      steps {
        script {
          def img = docker.image('python:3.9')
          img.pull()
          img.inside('-u root:root') {
            checkout scm
            sh 'pip install pyflakes pytest'
            sh 'pyflakes *.py'
            sh 'pytest --maxfail=1 --disable-warnings -q'
          }
        }
      }
    }
  }

  post {
    success {
      echo 'Build & Tests erfolgreich'
    }
    failure {
      echo 'Build fehlgeschlagen – Logs prüfen'
    }
  }
}
