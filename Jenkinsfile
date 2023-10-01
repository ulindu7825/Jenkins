pipeline {
    agent any
   
    stages {
        stage('Build') {
            steps {
               
                echo "Building launched using Maven"
                echo "Build successful"
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo "Unit tests launched with NUint"
                echo "Unit tests successful."
                echo "Integration tests started with Selenium"
                echo "Integration tests successful."
            }
            
       post {
        success {
            echo "Unit and Integration Tests stage is completed."  // Input the line when debugging
            emailext(
                to: 'ulinduperera434@gmail.com',
                subject:"Current Stage Status:  ${currentBuild.result}",
                body:"Please check the log file attached to the email for details.",
                attachLog: true
            )
        }
        failure {
            echo "Unit and Integration Tests stage failed"  // Input the line when debugging
            emailext(
                to: 'ulinduperera434@gmail.com',
                subject:"Current Stage Status:  ${currentBuild.result}",
                body:"Please check the log file attached to the email for details.",
                attachLog: true
            )
        }
    }
        }

        stage('Code Analysis') {
            steps {
                echo "Code analysis initiated with Veracode"
                echo "Code analysis successfully completed"
            }
        }

        stage('Security Scan') {
            steps {
                echo "Security scans initiated with 42Crunch"
                echo "Security scans successfully completed"
            }
            
                   post {
        success {
            echo "Unit and Integration Tests stage completed"  // Input the line when debugging
            emailext(
                to: 'ulinduperera434@gmail.com',
                subject:"Current Stage Status:  ${currentBuild.result}",
                body:"Please check the log file attached to the email for details.",
                attachLog: true
            )
        }

        failure {
            echo "Security Scan Test stage failed"  // Input the line when debugging
            emailext(
                to: 'ulinduperera434@gmail.com',
                subject:"Current Stage Status:  ${currentBuild.result}",
                body:"Please check the log file attached to the email for details.",
                attachLog: true
            )
        }
    }
    }

        stage('Deploy to Staging') {
            steps {
                echo "Stage deployment initiated"
                echo "Deployed to AWS EC2 instance-id: i-4214535890abcdef0 staging server"
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo "Integration tests initiated with Selenium"
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
