pipeline{
  agent any
  stages{
    stage("Git Checkout"){
      steps{
            git credentialsId: 'github', url: 'https://github.com/aditya-malviya/myweb.git'
           }
          }
     stage("Maven Build"){
       steps{
            sh "mvn clean package"
            sh "mv target/*.war target/myweb.war"
             }
            }
     stage("deploy-dev"){
       steps{
          sshagent(['ubuntu02']) {
          sh """
          scp -o StrictHostKeyChecking=no target/myweb.war  
          ubuntu@13.233.190.209:/var/lib/tomcat9/webapps/ROOT/
          ssh ubuntu@13.233.190.209 /usr/share/tomcat9/bin/shutdown.sh
          ssh ubuntu@13.233.190.209 /usr/share/tomcat9/bin/startup.sh
           """
            }
          }
        }
      }
    }
