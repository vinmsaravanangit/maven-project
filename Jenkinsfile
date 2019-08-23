pipeline {
    agent any
   tools {
        maven 'localMaven' 
    }
    stages {
        stage('Build') {
            steps {
                 mvn 'clean package'
            }
            post{
                success{
                    echo 'Now archiving...'
                    archiveartifacts artifacts: '**/target/*.war'
                }
            }

        }

        }
}