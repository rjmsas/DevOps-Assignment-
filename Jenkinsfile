pipeline {
    agent 
    {
        label 'control'
    }
    stages 
    {
        stage ('rebuild-docker-image')
        {
            steps
            {
                sh '''
                docker build -t tomcat-v3 .
                '''
            }
        }
        stage('deploy-tomcat')
        {
            steps
            {
                sh '''
                docker-compose -f tomcat-compose.yml down
                docker-compose -f tomcat-compose.yml up -d
                '''
            }
        }
    }
}