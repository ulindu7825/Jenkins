pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    echo "Use Maven"
                    currentBuild.rawBuild.getLog(1000).each { line ->
                        echo "Build: $line"
                    }
                }
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                script {
                    echo "Use NPM Test"
                    currentBuild.rawBuild.getLog(1000).each { line ->
                        echo "Unit and Integration Tests: $line"
                    }
                }
            }
        }
        stage('Code Analysis') {
            steps {
                script {
                    echo "Try Sonar-Scanner"
                    currentBuild.rawBuild.getLog(1000).each { line ->
                        echo "Code Analysis: $line"
                    }
                }
            }
        }
        stage('Security Scan') {
            steps {
                script {
                    echo "Use a security scanning tool to identify vulnerabilities"
                    echo "Trying npm audit"
                    currentBuild.rawBuild.getLog(1000).each { line ->
                        echo "Security Scan: $line"
                    }
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                script {
                    echo "Use AWS CLI or other deployment tool to deploy to staging"
                    currentBuild.rawBuild.getLog(1000).each { line ->
                        echo "Deploy to Staging: $line"
                    }
                }
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo "Running"
                    currentBuild.rawBuild.getLog(1000).each { line ->
                        echo "Integration Tests on Staging: $line"
                    }
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                script {
                    echo "Use AWS CLI or other deployment tool to deploy to production"
                    currentBuild.rawBuild.getLog(1000).each { line ->
                        echo "Deploy to Production: $line"
                    }
                }
            }
        }
    }
    post {
        success {
            script {
                def emailBody = ""
                currentBuild.rawBuild.getLog(1000).each { line ->
                    emailBody += line + '\n'
                }
                mail to: "harshitbal80@gmail.com",
                     subject: "Build Successful: ${currentBuild.fullDisplayName}",
                     body: "The build was successful.\n\nLogs:\n\n$emailBody"
            }
        }
        failure {
            script {
                def emailBody = ""
                currentBuild.rawBuild.getLog(1000).each { line ->
                    emailBody += line + '\n'
                }
                mail to: "harshitbal80@gmail.com",
                     subject: "Build Failed: ${currentBuild.fullDisplayName}",
                     body: "The build has failed. Please check the logs for details.\n\nLogs:\n\n$emailBody"
            }
        }
    }
}
