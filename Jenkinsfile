pipeline {
    agent any

    tools {
        maven 'Maven'  // Change if your Jenkins Maven installation name differs
        jdk 'JDK17'    // Change if your Jenkins JDK name differs
    }

    stages {
        stage('Checkout Code') {
            steps {
                git url: 'https://github.com/manaswini-k10/DemoApp.git',
                    branch: 'main',
                    credentialsId: 'github-pat-manaswini'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean package'   // Use 'sh' instead of 'bat' if Jenkins is on Linux
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
            }
        }
    }

    post {
        success {
            echo '✅ Build Successful!'
        }
        failure {
            echo '❌ Build Failed!'
        }
    }
}
