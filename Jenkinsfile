pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh 'composer install'
      }
    }

    stage('test') {
      parallel {
        stage('unitaire') {
          steps {
            sh 'php bin/phpunit tests/unit'
          }
        }

        stage('integration') {
          steps {
            sh 'php bin/phpunit tests/integration'
          }
        }

        stage('functional') {
          steps {
            sh 'php bin/phpunit tests/functional'
          }
        }

      }
    }

    stage('deploy') {
      steps {
        sh 'symfony server:start'
      }
    }

  }
}