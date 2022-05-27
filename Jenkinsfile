pipeline{
    agent any
    tools{
        maven 'maven'
    }
    
    stages {
        stage ('Build'){
            steps {
                sh 'mvn clean install package'
            }
        }

        stage ('Test'){
            steps {
                echo 'Testing ...'
            }
        }

        stage ('Deploy'){
            steps {
                echo 'Deploying ...'
            }            
        }
    }
}