pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }
    stage('Install Dependencies') {
      steps {
        sh 'pip install pyflakes pytest'
      }
    }
    stage('Lint') {
      steps {
        sh 'pyflakes *.py'
      }
    }
    stage('Test') {
      steps {
        sh 'pytest --maxfail=1 --disable-warnings -q'
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

