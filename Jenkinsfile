pipeline {
    agent any

    tools {
        jdk 'jdk-21'
        maven 'maven 3.9.12'
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('soanarqube-server') {
                    sh 'mvn clean package sonar:sonar -Dsonar.projectKey=mvnapp-org1_mvn-project -Dsonar.projectName=mvn-project -Dsonar.organization=mvnapp-org1 -Dsonar.host.url=https://sonarcloud.io/ -Dsonar.login=28a71b5f313e512699e6d02857092b0ae62bd437 -X'
                }
            }
        }
    }
}