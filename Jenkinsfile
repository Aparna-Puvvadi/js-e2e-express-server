pipeline
{
    agent any
    stages
    {
        stage('source code'){
            steps{
                git branch: 'main', url: 'https://github.com/Azure-Samples/js-e2e-express-server.git'
            }
        }
        stage('dependencies'){
            steps{
                sh 'npm install'
            }
        }
        stage('test'){  
            steps{
                sh "npm test"    
           }              
        }
        stage("sonar analysis") {
            steps {
                withSonarQubeEnv(installationName: 'SONAR_9.4', envOnly: true, credentialsId: 'SONAR_TOKEN') {
                    sh "npm run sonar"
                    echo "${env.SONAR_HOST_URL}"
                }    
            }
        }
        stage('Build the code'){
            steps{
                   sh 'npm run build'
            }
        }
        stage('archiving the reports'){
            steps{
                sh 'npm pack'
            }
        }
    }
}