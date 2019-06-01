pipeline {
  agent {
    docker {
      image 'php:7.2'
      args '-u root:sudo'
    }

  }
  stages {
    stage('Build') {
      steps {
        
        sh '''
                    apt install php7.2-bcmath
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
