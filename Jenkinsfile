pipeline{
    agent any
   
    stages{
        stage('Build'){
            steps{
                echo "Bulding Initiated using Maven"
                echo "Build succesfully"
            }
        }

        stage('Unit and Integration Tests'){
            steps{
                echo "Unit tests Initiated with NUint"
                echo "Unit tests completed."
                echo "Intergration tests started with Selenium"
                echo "Intergration tests completed."
            }
            post {
                failure {
                    emailext(
                        to: 'ulinduperera434@gmail.com',
                        subject: "Unit and Integration Test Failed",
                        body: 'Unit and Integration Test failed. Please check attached logs for more details.',
                        attachLog: true 
                    )      
                }
                success {
                    emailext(
                        to: 'ulinduperera434@gmail.com',
                        subject: 'Unit and Integration Test Succeeded',
                        body: 'Unit and Integration Test succeeded.Please Check attached logs for more details.',
                        attachLog: true     
                    ) 
                }
            }

        }

        stage('Code Analysis'){
            steps{
                echo "Code analysis started with Veracode"
                echo "Code analysis succesfully completed"
            }
        }

        stage('Security Scan'){
            steps{
                echo "Security scans started with 42Crunch"
                echo "Security scans succesfully completed"
            }
            post {
                failure {
                    emailext(
                        to: 'ulinduperera434@gmail.com',
                        subject: 'Security Scan Failed',
                        body: 'Security Scan failed.Please Check attached logs for more details.',
                        attachLog: true  
                    ) 
                }
                success {
                    emailext(
                        to: 'ulinduperera434@gmail.com',
                        subject: 'Security Scan Succeeded',
                        body: 'Security Scan succeeded.Please check attached logs for details.',
                        attachLog: true 
                    )   
                }
            }
        }

        stage('Deploy to Staging'){
            steps{
                echo "Stagging deployment started"
                echo "Deployed to AWS EC2 instance-id: i-4214535890abcdef0 staging server"
            }
        }

        stage('Integration Tests on Staging'){
            steps{
                echo "Intergration tests started with Selenium"
                echo "Intergration tests completed succesfully."
            }
        }

        stage('Deploy to Production') {
            steps {
                echo "Stagging deployment started"
                echo "Deployed to AWS EC2 instance-i-4214535890abcdef0 staging server"
            }
        }
    }
}
