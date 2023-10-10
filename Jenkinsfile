pipeline {
    agent any
    tools{
        jdk 'jdk17'
    }
   
    stages {
        stage('git checkout') {
            steps {
                git 'https://github.com/KARTHIZz/rds_php.git'
            }
        }
        
        stage('trivy fs') {
            steps {
               sh "trivy fs ."
            }
        }
        

        
        
        stage('docker image') {
            steps {
                script{
                     
                        sh "docker build -t php_app ."
                }

            }
        }
       
        
        
        stage('docker deploy') {
            steps {
                script{
                    
                        sh "docker run -d -p 8090:80 php_app"
                    
                }
            }
        }
    }
}
