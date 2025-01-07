pipeline {
    agent any

    triggers {
        pollSCM '* * * * *'
    }

    stages {
        stage('Maven-Build') {
            steps {
                su '''
                cd yan-maven-docker-project
                mvn clean install
                '''
            }            
        }  

         stage('Docker-Build') {
            steps {
                su '''
                cd yan-maven-docker-project
                docker build -t java-image:v1 .
                '''    
            }            
        }  
    }

}



