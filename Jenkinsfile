pipeline
{
    agent any
    stages
    {
        stage('GitHub ')
        {
            steps
            {
                git branch: 'main', credentialsId: 'web-app-jenkins', url: 'https://github.com/ahmedsamyabdullah/web-app.git'
            }
        }
        stage('Validate HTML') {
            steps {
                sh 'htmlhint index.html || true'
            }
        }
        stage('Validate CSS') {
            steps {
                sh 'stylelint style.css || true'
            }
        }
    }
}