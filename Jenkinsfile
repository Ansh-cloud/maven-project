pipeline {
    agent any
    stages{
        stage('clone') {
            steps{
                git 'https://github.com/Ansh-cloud/maven-project.git'
            }
            
        }
        stage('Build') {
            steps{
                sh 'mvn clean package'
            }
            post{
                success{
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
        stage('Deploy-stage'){
            steps{
                build job: 'deploy-staging'
            }
            post{
                success{
                    echo 'code deployed to stage'
                }
                failure{
                    echo 'deployment failed'
                }
            }
        }
    }
}