node('master') 
{
    stage('ContinuesDownload') 
        {
             git 'https://github.com/balajimbk/maven-pro.git'
        }
    
    stage('ContinuesBuild') 
        {
            sh label: '', script: 'mvn package'
         }
    
    stage('ContinuesDeployment') 
         {
            sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/Pipeline/webapp/target/webapp.war  ubuntu@172.31.1.225:/var/lib/tomcat8/webapps/qaenv.war'
                     }
         
    stage('ContinueTesting')
        {
            git 'https://github.com/balajimbk/Functional_Testing.git'
            sh label: '', script: 'java -jar /home/ubuntu/.jenkins/workspace/Pipeline/testing.jar'
        }
    stage('ContinuesDelivery')
        {
                input message: 'Waiting for approval from DM'
                sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/Pipeline/webapp/target/webapp.war  ubuntu@172.31.1.160:/var/lib/tomcat8/webapps/prodevn.war'
        }
        
}

