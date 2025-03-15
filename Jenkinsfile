pipeline
{
    // Specifiy Agent
    agent any
    // Environment Variables
    environment
    {
        SONAR_PROJECT_KEY   = 'web-app-jenkins'
        SONAR_SCANNER_HOME  =  tool 'sonarqubescanner'
    }
    stages
    {
        // GitHub Repo 
        stage('GitHub ')
        {
            steps
            {
                git branch: 'main', credentialsId: 'web-app-jenkins', url: 'https://github.com/ahmedsamyabdullah/web-app.git'
            }
        }
         // SonarQube With Jenkins
        stage('sonarqube analysis')
        {
            steps
            {
                withCredentials([string(credentialsId: 'sonar-jenkins-token', variable: 'sonar_token')]) 
                {
                    withSonarQubeEnv('sonarqube') 
                    {
                       sh """
                         ${SONAR_SCANNER_HOME}/usr/local/bin/sonar-scanner \
                         -Dsonar.projectKey=${SONAR_PROJECT_KEY} \
                         -Dsonar.sources=. \
                         -Dsonar.host.url=http://192.168.1.82:9000 \
                         -Dsonar.login=${sonar_token}
                       """
                    }
                }
            }
        }
    }
}