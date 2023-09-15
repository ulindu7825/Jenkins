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
                success {
                        mail to:"ulinduperera44@gmail.com",
                        subject: "Build Successful: ${currentBuild.fullDisplayName}",
                        body: "The build was successful. \n Unit and Integration Tests: ${attachLog: true}"
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
             post {
                success {
                        mail to:"ulinduperera44@gmail.com",
                        subject: "Build Successful: ${currentBuild.fullDisplayName}",
                        body: "The build was successful. \n Security Scan: ${attachLog: true}"
                }
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
