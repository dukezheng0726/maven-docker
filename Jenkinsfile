pipeline {
    agent any
    triggers {
        pollSCM '* * * * *'
    }

    stages {
        stage("step1") {
            steps {
                su '''
                cd yan-maven-docker-project
                mvn clean install          
                '''
            }
        }

        stage("step2") {
            steps {
                su '''
                cd yan-maven-docker-project
                echo "Building Docker"
                docker build -t java-image:v1 .           
                '''
            } 
        }
    }
}