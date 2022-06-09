node('built-in') 
{
    stage('ContinuousDownload') 
    {
         git 'https://github.com/Kalagbor/maven8.git'
    }
    stage('ContinuousBuild') 
    {
         sh 'mvn package'
    } 
    stage ('ContinuousDeployment')
    {
         deploy adapters: [tomcat9(credentialsId: 'd100bb38-b0cc-4166-a706-5ddf6c094fdf', path: '', url: 'http://172.31.1.115:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('ContinuousTesting')
    {
       git 'https://github.com/intelliqittrainings/FunctionalTesting.git' 
       sh 'java -jar /var/lib/jenkins/workspace/Scriptedpipeline2/testing.jar'
    }
    stage('ContinuousDelivery')
    {
        
    deploy adapters: [tomcat9(credentialsId: 'd100bb38-b0cc-4166-a706-5ddf6c094fdf', path: '', url: 'http://172.31.4.43:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
    
}
