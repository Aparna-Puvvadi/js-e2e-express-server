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
        stage('start the service'){
            steps{
                sh 'npm start &'
            }
        }
    }
}