pipeline {
	agent {
		docker {
			   image 'php:latest'
		}
	}
	stage('Prepare') {
            steps {
                sh 'apt-get update && apt-get install -y curl php-cli php-mbstring git unzip'
                sh 'curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer'
            }
        }
	stages {
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