pipeline{
    //Directives
    agent any
    tools {
        maven 'maven'
    }

    environment {
        ArtifactId = readMavenPom().getArtifactId()
        Version = readMavenPom().getVersion()
        Name = readMavenPom().getName()
        GroupId = readMavenPom.getGroupId()
    }

    stages {
        // Specify various stage with in stages        
        stage ('Build'){
            steps {
                sh 'mvn clean install package'
            }
        }

        // Stage2 : Testing
        stage ('Test'){
            steps {
                echo 'testing......'
            }
        }

        // Stage3 : Publishing artifacts to Nexus
        stage ('Publish to Nexus'){
            steps{
                nexusArtifactUploader artifacts: [[artifactId: '${ArtifactId}', classifier: '', file: 'target/JoesDevOpsLab-0.0.4.war', type: 'war']], credentialsId: 'a70083c1-9d77-4ab3-9b96-6e61d067fd4b', groupId: '${GroupId}', nexusUrl: '172.20.10.176:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'JoesDevopsLab-Snapshot', version: '${VersionId}'
            }
        }

        stage ('print values'){
            steps{
                echo "Artifact ID is '${ArtifactId}'"
                echo "Version is '${Version}'"
                echo "Name is '${Name}'"
                echo "Group ID is '${GroupId}'"
            }
        }
        // Stage3 : Publish the source code to Sonarqube
        stage ('Deploy'){
            steps {
                echo 'Deploying...'
                }
            }
    }      
        
}