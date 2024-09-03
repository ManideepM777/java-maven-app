pipeline{
    agent { label 'Jenkins-Agent'}
    tools{
        jdk 'Java17'
        maven 'Maven3'
    }
    stages{
        stage("Cleanup Worksapce"){
            steps{
                cleanWs()
            }
        }
        stage("Check out from SCM"){
            steps{
                git branch: 'main', credentialsId: 'github', url: 'https://github.com/mihirmodi2561/register-app'
            }
        }
        stage("Build Application"){
            steps{
                sh "mvn clean package"
            }
        }
        stage("Test Application"){
            steps{
                sh "mvn test"
            }
        }
    }
}    
