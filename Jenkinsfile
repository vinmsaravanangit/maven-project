pipeline {
    agent any
  
    stages {
        stage('Build') {
            steps {
               
                        bat 'mvn clean package'
                 
            }
            post{
                success{
                    echo 'Now archiving...'
                   
                    archiveArtifacts '**/target/*.war'
                }
            }

        }
        stage('Deploy to Staging') {
            steps{
                build job: 'deploy-to-staging'
            }
        }

        stage('Deploy to Production') {
            steps{
                timeout(time:5, unit:'DAYS'){
                    input message:'Approve PROD Deployment?'
                }
                
                build job: 'deploy-to-prod'
            }
            post{
                success{
                    echo 'Code DEPLOYED TO PROD'
                }
                failure{
                    echo 'DEPLOYMENT FAILED'
                }
            }
        }

        }
}
