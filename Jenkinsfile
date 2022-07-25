pipeline {
    agent any

    stages {
        stage('Build and Sonar') {
            steps {
                sh './mvnw clean'
                sh './mvnw package'
                sh './mvnw org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar -Dsonar.projectKey=pet-clinic -Dsonar.host.url=http://sonarqube:9000 -Dsonar.login=4d83d677f7614edf35d51285d2af748cdb5b1684'
            }
        }
    }
}