node('built-in') 
{
    stage('Continuous Download') 
    {
        git 'https://github.com/FonsahPageo/maven.git'
    }
    stage('Continuous Build') 
    {
        sh 'mvn package'
    }
    stage('Continuous Deploy') 
    {
        sh 'scp /var/lib/jenkins/workspace/scriptedpipeline/webapp/target/webapp.war ubuntu@172.31.34.102:/var/lib/tomcat9/webapps/qaenv.war'
    }
    stage('Continuous Delivery') 
    {
        sh 'scp /var/lib/jenkins/workspace/scriptedpipeline/webapp/target/webapp.war ubuntu@172.31.41.225:/var/lib/tomcat9/webapps/prodenv.war'
    }
    stage("Email Notification")
    {
        mail bcc: '', body: 'Alert for scriptedpipeline job', cc: '', from: '', replyTo: '', subject: 'Scripted pipeline job', to: 'ashprincepageo@gmail.com'
    }
}
