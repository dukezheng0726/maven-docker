pipeline{
    agent any
    triggers{
        pollSCM '* * * * *'
    }
    stages{
        stage('1'){
            steps{
                sh '''
                cd yan-maven-docker-project
                mvn clean install                    
                '''
            }
        }
        stage('2'){
            steps{
                sh '''
                cd yan-maven-docker-project
                echo "Building Docker"
                docker build -t java-image:v1 .      
                '''
            }
        }
    }
}