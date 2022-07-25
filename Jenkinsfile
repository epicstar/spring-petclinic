pipeline {
    agent any

    stages {
        stage('Build and Sonar') {
            steps {
                sh './mvnw clean package org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar -Dsonar.projectKey=pet-clinic -Dsonar.host.url=http://sonarqube:9000 -Dsonar.login=hw1'
                sh 'java -jar target/*.jar'
            }
        }
    }
}