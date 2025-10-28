pipeline{
    agent any
    tools{
        maven 'local_maven'
    }

    stages{
        stage ('Build'){
            steps{
                sh 'mvn clean pkg'
            }
            post{
                success{
                    echo "Archiving the Artifcats"
                    archiveArtifacts artifacts: '/**/target/*.war'
                
                }
            }
        }
        stage('Deploy to tomcat server'){
            steps{
                deploy adapters: [tomcat8(alternativeDeploymentContext: '', credentialsId: '848be0fb-47d7-4e0f-a36f-f834f3c52629', path: '', url: 'http://localhost:8080/')], contextPath: null, war: '**/*.war'
            }

        }
    }
}