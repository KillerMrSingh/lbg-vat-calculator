pipeline {
	agent any

	stages {
		stage('Checkout'){
			steps {
				git branch: 'main', url: 'https://github.com/KillerMrSingh/lbg-vat-calculato/'
			}
		}
		stage('SQ-Jenkins-Test'){
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
