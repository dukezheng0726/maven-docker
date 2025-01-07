pipeline {
    agent { 
        node {
            label 'docker-agent-python'
            }
      }
    triggers {
        pollSCM '* * * * *'
    }
    stages {
        stage('Build') {
            steps {
                echo "Building.."
                sh '''
                cd myapp
                pip install -r requirements.txt
                '''
            }
        }
        stage('Test') {
            steps {
                echo "Testing.."
                sh '''
                cd myapp
                python3 hello.py
                python3 hello.py --name=Brad
                '''
            }
        }
        stage('Deliver') {
            steps {
                echo 'Deliver....'
                sh '''
                echo "doing delivery stuff.."
                '''
            }
        }
    }
}


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

        //  stage('Docker-Run') {
        //     steps {
        //         su '''
        //         docker run -p 8090:8080 java-image:v1
        //         '''    
        //     }            
        // }  

    }

}



