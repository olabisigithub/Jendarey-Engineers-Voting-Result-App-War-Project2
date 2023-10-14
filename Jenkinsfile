pipeline {
    agent any
    tools {
        maven "MAVEN3"
        jdk "OracleJDK17"
    }

    stages {
        stage('1-Fetch Code') {
            steps {
                sh "echo 'cloning the latest application version'"
                git branch: 'master', url: 'https://github.com/JendareyTechnologies/Jendarey-Engineers-Voting-Result-App-War-Project2.git'
            }
        }
        stage('2-Build') {
            steps {
                sh "echo 'cleaning and build packages'"
                sh 'mvn clean install -DskipTests'
            }
            post {
                always {
                    echo 'Archiving artifacts now.'
                    archiveArtifacts artifacts: '**/*.war', allowEmptyArchive: true
                }
            }
        }
        stage('3-Unit Test') {
            steps {
                sh "echo 'running JUnit-test-cases' "
                sh "echo 'testing must passed to create artifacts ' "
                sh 'mvn test'
            }
        }
    }
}
