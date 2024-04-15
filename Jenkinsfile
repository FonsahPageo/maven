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
    // replace ip with the private IP of the qa/prod server
    stage('Continuous Delivery') 
    {
        sh 'scp /var/lib/jenkins/workspace/scriptedpipeline/webapp/target/webapp.war ubuntu@172.31.41.225:/var/lib/tomcat9/webapps/prodenv.war'
    }
    // This is to test the webhook
    stage("Email Notification")
     {
        mail (
            bcc: '', 
            body: "${env.JOB_NAME} - Build # ${env.BUILD_NUMBER} - ${currentBuild.currentResult}: Check console output at ${env.BUILD_URL} to view the results. This is an auto-generated email. Do not reply.",
            cc: '', 
            from: '', 
            replyTo: '', 
            subject: "${env.JOB_NAME} - Build # ${env.BUILD_NUMBER} - ${currentBuild.currentResult}!",
            to: 'ashprincepageo@gmail.com'
        )
    }
}
