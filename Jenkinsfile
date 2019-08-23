pipeline {
    agent any
  
    stages {
        stage('Build') {
            steps {
                maven(maven : 'localMaven'){
                        bat 'mvn clean package'
                 
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
}