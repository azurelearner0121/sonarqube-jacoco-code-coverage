pipeline {
    agent { label 'dev-agent'}
    stages {
   stage('Clone sources') {
            steps {
                git url: 'https://github.com/azurelearner0121/sonarqube-jacoco-code-coverage.git'
            }
        }
        stage('SonarQube analysis') {
            steps {
                withSonarQubeEnv('sonarqubeserver') {
                    sh "./gradlew sonarqube"
                }
            }
        }
        stage("Quality gate") {
            steps {
                waitForQualityGate abortPipeline: true
            }
        }
    }
}
