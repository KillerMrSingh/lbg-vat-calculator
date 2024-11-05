pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/KillerMrSingh/lbg-vat-calculator/'
            }
        }
        stage('SonarQube Analysis') {
            environment {
                scannerHome = tool 'sonarqube'
            }
            steps {
                withSonarQubeEnv('MySonarQubeServer') {  // Replace with your actual SonarQube configuration name
                    withCredentials([string(credentialsId: 'sonar-auth-token', variable: 'sqa_08d0210bbb64910b4984732e9586db96df844d08')]) {
                        sh """
                        ${scannerHome}/bin/sonar-scanner \
                        -Dsonar.projectKey=your_project_key \
                        -Dsonar.sources=. \
                        -Dsonar.login=$SONAR_AUTH_TOKEN
                        """
                    }
                }
            }
        }
    }
}
