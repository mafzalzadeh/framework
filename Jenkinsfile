pipeline {
  agent {
    docker {
      image 'php:7.3'
      args '-u root:sudo'
    }

  }
  stages {
    stage('Build') {
      steps {
        
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
