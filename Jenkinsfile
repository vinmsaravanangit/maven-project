pipeline{
    agent any
    stages{
        stage{
            steps('Build')
            {
                bat 'mvn clean package'
            }
        }
    }
}