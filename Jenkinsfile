pipeline {
	agent any
	stages {
		stage('Build') {
			steps {
				def installResult = sh(script: 'composer install', returnStatus: true)
        if (installResult != 0) {
            error 'Composer install failed'
        }
			}
		}
		stage('Test') {
			steps {
                sh './vendor/bin/phpunit tests'
            }
		}
	}
}