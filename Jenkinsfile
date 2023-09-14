pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo "Used Maven for the task"
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "Applied the NPM Test"
            }
        }
        stage('Code Analysis') {
            steps {
                echo "Applied Sonar-Scanner"
            }
        }
        stage('Security Scan') {
            steps {
                echo "Applied the security scanning tool to identify vulnerabilities"
                echo "Trying npm audit"
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "Apply AWS CLI or another deployment tool to deploy to staging"
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "Running"
            }
            post {
                success {
                    archiveArtifacts artifacts: '**/target/*.log', allowEmptyArchive: true
                    emailext subject: "Build Successful: ${currentBuild.fullDisplayName}",
                              body: "The build was successful.",
                              attachmentsPattern: '**/target/*.log',
                              to: 'viranthamudalige@gmail.com'
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Apply AWS CLI or another deployment tool to deploy to production"
            }
        }
    }
}
