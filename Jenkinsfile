pipeline {
    agent any
    parameters{
        string(name:'tomcat_dev', defaultValue:'18.232.106.248', description:'Staging Server')
        string(name:'tomcat_prod', defaultValue:'3.82.55.51', description:'Prodcution Server')
    }

    trigers{

        pollSCM('* * * * *')
    }
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
        stage('Deployments') {
            parallel{
                stage('Deployment to Staging')
                {
                    steps {
                        sh "scp -i C:\\Users\\91956\\Desktop\\tomcat-demo.pem **/target/*.war ec2-user@${params.tomcat_dev}:/var/lib/tomcat/webapps"
                    }
                }
                 stage('Deployment to Production')
                {
                    steps {
                        sh "scp -i C:\\Users\\91956\\Desktop\\tomcat-demo.pem **/target/*.war ec2-user@${params.tomcat_prod}:/var/lib/tomcat/webapps"
                    }
                }

            }
        }

        
        }
}
