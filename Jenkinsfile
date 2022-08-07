pipeline {
    agent any

    environment {
        SONARQUBE_LOGIN = credentials("sonarqube-petclinic")
    }

    stages {
        stage('Build and Sonar') {
            steps {
                sh './mvnw clean'
                sh './mvnw package'
                sh './mvnw org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar -Dsonar.projectKey=pet-clinic -Dsonar.host.url=http://sonarqube:9000 -Dsonar.login=$SONARQUBE_LOGIN'
            }
        }
        stage('Deploy') {
            steps {
                ansiblePlaybook(credentialsId: 'petclinic-webserver-creds', inventory: 'ansible-config/inventory.yml', playbook: 'playbook.yml')
            }
        }
    }
}
