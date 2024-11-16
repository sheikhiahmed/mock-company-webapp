
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Pull the latest code from the repository
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // Run the Gradle assemble task
                sh './gradlew assemble'
            }
        }

        stage('Test') {
            steps {
                // Run the Gradle test task
                sh './gradlew test'
            }
        }
    }

    post {
        always {
            // Archive test results and logs
            junit '**/build/test-results/**/*.xml'
            archiveArtifacts artifacts: '**/build/libs/*.jar', fingerprint: true
        }
    }
}
