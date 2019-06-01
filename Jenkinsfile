pipeline {
  agent {
    docker {
      image 'php:7.0'
      args '-u root:sudo'
    }

  }
  stages {
    stage('Build') {
      steps {
        sh '''apt-get update -q
                apt-get install git -y
                apt-get autoremove graphviz -y
                apt-get install graphviz -y
                '''
        sh '''
                    echo $USER
                    php -r "copy(\'https://getcomposer.org/installer\', \'composer-setup.php\');"
                    php composer-setup.php
                    php -r "unlink(\'composer-setup.php\');"
                    php composer.phar self-update
                    php composer.phar install --no-interaction
                    ls -la
                    vendor/bin/phpunit
                '''
      }
    }
  }
}
