pipeline {
    agent any
    triggers {
        pollSCM '* * * * *'
    }

    stages {
        stage("Maven-Build") {
            steps {
                sh '''
                
                cd yan-maven-docker-project
                mvn clean install

                '''
            }
        }

        stage("Docker-Build") {
            steps {
                sh '''
                cd yan-maven-docker-project
                echo "Building Docker"
                docker build -t java-image:v1 .
                '''
                // 
            }
        }
    }
}