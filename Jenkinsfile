pipeline
{
    agent any
    stages
    {
        stage('continousdwonload')
        {
            steps
            {
                git '  https://github.com/SureshReddy03/mavennew.git '
            }
        }
        stage('continousbuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('continousdeploy')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'a0304f23-4004-4b74-b893-57639ece5aaf', path: '', url: 'http://172.31.11.3:8080')], contextPath: 'qaserver', war: '**/*.war'
            }
        }
        stage('continoustesting')
        {
            steps
            {
                git '  https://github.com/intelliqittrainings/FunctionalTesting.git'
                
                sh 'java -jar /home/ubuntu/.jenkins/workspace/development/testing.jar'
                
            }
        }
        stage('continousdelivery')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'a0304f23-4004-4b74-b893-57639ece5aaf', path: '', url: 'http://172.31.9.236:8080')], contextPath: 'prodserver', war: '**/*.war'
            }
        }
    }
}
