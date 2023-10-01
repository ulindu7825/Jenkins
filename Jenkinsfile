pipeline {
    agent any
   
    stages {
        stage('Build') {
            steps {
                echo "Code fetched from https://github.com/manubalhara/Jenkins-Project.git"
                echo "Building Initiated using Maven"
                echo "Build successful"
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo "Unit tests Initiated with NUint"
                echo "Unit tests completed."
                echo "Integration tests started with Selenium"
                echo "Integration tests completed."
            }
            
       post {
        success {
            echo "Unit and Integration Tests stage succeeded"  // Add this line for debugging
            // Archive the log files or any other artifacts you want to attach to the email
            archiveArtifacts artifacts: '**/logs/*.log', allowEmptyArchive: true

            // Send an email with the archived log files
            emailext(
                to: 'harshitbal80@gmail.com',
                subject: "Build Status: ${currentBuild.result}",
                body: "Build Status: ${currentBuild.result}",
                attachmentsPattern: '**/logs/*.log'
            )
        }
    }
        }

        stage('Code Analysis') {
            steps {
                echo "Code analysis started with Veracode"
                echo "Code analysis successfully completed"
            }
        }

        stage('Security Scan') {
            steps {
                echo "Security scans started with 42Crunch"
                echo "Security scans successfully completed"
            }
            
            post {
                success {
                    mail to: "harshitbal80@gmail.com",
                    subject: "Security Scan Successful: ${currentBuild.fullDisplayName}",
                    body: "The security scan was successful."
                }
                failure {
                    mail to: "harshitbal80@gmail.com",
                    subject: "Security Scan Failed: ${currentBuild.fullDisplayName}",
                    body: "The security scan has failed. Please check the logs for details."
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo "Staging deployment started"
                echo "Deployed to AWS EC2 instance-id: i-4214535890abcdef0 staging server"
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo "Integration tests started with Selenium"
                echo "Integration tests completed successfully."
            }
        }

        stage('Deploy to Production') {
            steps {
                echo "Production deployment started"
                echo "Deployed to AWS EC2 instance-i-4214535890abcdef0 production server"
            }
        }
    }
}
