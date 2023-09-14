pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                catchError(buildResult: 'SUCCESS', stageResult: 'SUCCESS') {
                    echo "Used Maven for the task"
                }
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                catchError(buildResult: 'SUCCESS', stageResult: 'SUCCESS') {
                    echo "Applied the NPM Test"
                }
            }
        }
        stage('Code Analysis') {
            steps {
                catchError(buildResult: 'SUCCESS', stageResult: 'SUCCESS') {
                    echo "Applied Sonar-Scanner"
                }
            }
        }
        stage('Security Scan') {
            steps {
                catchError(buildResult: 'SUCCESS', stageResult: 'SUCCESS') {
                    echo "Applied the security scanning tool to identify vulnerabilities"
                    echo "Trying npm audit"
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                catchError(buildResult: 'SUCCESS', stageResult: 'SUCCESS') {
                    echo "Apply AWS CLI or another deployment tool to deploy to staging"
                }
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                catchError(buildResult: 'SUCCESS', stageResult: 'SUCCESS') {
                    echo "Running"
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                catchError(buildResult: 'SUCCESS', stageResult: 'SUCCESS') {
                    echo "Apply AWS CLI or another deployment tool to deploy to production"
                }
            }
        }
    }
    post {
        success {
            
                def emailBody = ""
                    for (stage in currentBuild.builds) {
                        emailBody += "Stage: ${stage.result.displayName}\n"
                        emailBody += "Logs:\n${stage.log}\n\n"
                
                mail to: "ulinduperera434@gmail.com",
                subject: "Build Successful: ${currentBuild.fullDisplayName}",
                body: "The build was successful.\n\n${emailBody}"
            }
        }
    }
}
