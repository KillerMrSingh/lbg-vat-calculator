pipeline {
	agent any

	stages {
		stage('Checkout'){
			steps {
				git branch: 'main', url: 'https://github.com/KillerMrSingh/lbg-vat-calculator/'
			}
		}
		stage('jenkins-sonarqube-test-job'){
			environment {
				scannerHome = tool 'sonarqube'
			}
				steps {
					withSonarQubeEnv('sq-token') {
						sh "${scannerHome}/bin/sonar-scanner"
					}
				}
		}
	}
}
