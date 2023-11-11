pipeline {
	agent any
	
	stages {
		stage('Install Composer') {
            steps {
                script {
                    sh 'wget https://getcomposer.org/installer -O composer-setup.php'
                    sh 'php composer-setup.php --install-dir=/usr/local/bin --filename=composer'
                    sh 'php -r "unlink(\'composer-setup.php\');"'
                }
            }
        }
		stage('Build') {
			steps {
				sh 'composer install'
			}
		}
		stage('Test') {
			steps {
                sh './vendor/bin/phpunit tests'
            }
		}
	}
}