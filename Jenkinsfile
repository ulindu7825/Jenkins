pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo "Use Maven"
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "Use NPM Test"
            }
        }
        stage('Code Analysis') {
            steps {
                echo "Try Sonar-Scanner"
            }
        }
        stage('Security Scan') {
            steps {
                echo "Use a security scanning tool to identify vulnerabilities"
                echo "Trying npm audit"
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "Use AWS CLI or other deployment tool to deploy to staging"
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "Running"
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Use AWS CLI or other deployment tool to deploy to production"
            }
        }
    }
    post {
        success {
                mail to:"ulinduperera434@gmail.com",
                subject: "Build Successful: ${currentBuild.fullDisplayName}",
                body: "The build was successful."
                }
        }
}
