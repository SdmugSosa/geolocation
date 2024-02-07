pipeline {
    agent any
    tools {
        maven 'M2_HOME'
    }
    stages {
        stage('sonarqube scan') {
            steps {
                script {
                    // Make sure 'sonarqube' matches the configured SonarQube Scanner installation name
                    withSonarQubeEnv('sonarQube') {
                        sh 'mvn verify org.sonarsource.scanner.maven:sonar-maven-plugin:sonar -Dsonar.projectKey=SdmugSosa_geolocation -Dsonar.organization=sdmugsosa -Dsonar.host.url=https://sonarcloud.io -Dsonar.login=8a6b0b56f7f85c0c57fbedd0efd670c02c78ba8b'
                    }
                }
            }
        }
        stage('all maven commands') {
            steps {
                sh 'mvn clean install package'
            }
        }
    }
}
