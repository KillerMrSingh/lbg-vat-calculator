pipeline {
	agent any

	stages {
		stage('Checkout'){
			steps {
				git branch: 'main', url: 'https://github.com/KillerMrSingh/lbg-vat-calculato/'
			}
		}
		stage('SonarQube Analysis'){
			environment {
				scannerHome = tool 'sonarqube'
			}
				steps {
					withSonarQubeEnv('sonar-qube-1') {
						sh "${scannerHome}/bin/sonar-scanner"
					}
				}
		}
	}
}
