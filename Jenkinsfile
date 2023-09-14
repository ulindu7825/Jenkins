pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    currentStageLogs = bat(script: 'echo "Used Maven for the task"', returnStatus: true).trim()
                    echo currentStageLogs
                }
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                script {
                    currentStageLogs = bat(script: 'echo "Applied the NPM Test"', returnStatus: true).trim()
                    echo currentStageLogs
                }
            }
        }
        stage('Code Analysis') {
            steps {
                script {
                    currentStageLogs = bat(script: 'echo "Applied Sonar-Scanner"', returnStatus: true).trim()
                    echo currentStageLogs
                }
            }
        }
        stage('Security Scan') {
            steps {
                script {
                    currentStageLogs = bat(script: 'echo "Applied the security scanning tool to identify vulnerabilities"', returnStatus: true).trim()
                    currentStageLogs += '\n' + bat(script: 'npm audit', returnStatus: true).trim()
                    echo currentStageLogs
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                script {
                    currentStageLogs = bat(script: 'echo "Apply AWS CLI or another deployment tool to deploy to staging"', returnStatus: true).trim()
                    echo currentStageLogs
                }
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                script {
                    currentStageLogs = bat(script: 'echo "Running"', returnStatus: true).trim()
                    echo currentStageLogs
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                script {
                    currentStageLogs = bat(script: 'echo "Apply AWS CLI or another deployment tool to deploy to production"', returnStatus: true).trim()
                    echo currentStageLogs
                }
            }
        }
    }
    post {
        success {
            script {
                def emailBody = ""
                for (stage in currentBuild.builds) {
                    emailBody += "Stage: ${stage.result.displayName}\n"
                    emailBody += "Logs:\n${stage.log}\n\n"
                }
                mail to: "ulinduperera434@gmail.com",
                subject: "Build Successful: ${currentBuild.fullDisplayName}",
                body: "The build was successful.\n\n${emailBody}"
            }
        }
    }
}
