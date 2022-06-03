pipeline
{
    agent { label 'JDK8'}
    stages
    {
        stage('source code'){
            steps{
                git branch: 'main', credentialsId: '06ed9883-6839-494a-8a24-2bff76a3cdbe', url: 'https://github.com/Aparna-Puvvadi/nodejs.git'
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
                withSonarQubeEnv(installationName: 'SONAR_LATEST', envOnly: true, credentialsId: 'sonar') {
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