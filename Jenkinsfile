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
        stage('Deploy') {
            steps{
                build job: 'deploy-to-staging'
            }
        }

        }
}
