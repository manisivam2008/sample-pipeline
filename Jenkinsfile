node{
    def mavenHome= tool name: "maven", type: "maven"
    stage('Git Clone'){
        git url: 'https://github.com/shubh4527/maven-app.git'
    }
    stage('Build'){
        sh "${mavenHome}/bin/mvn clean package"
    }
    stage('deploy'){
         sshagent(['tomcat-dev']) {
         sh 'scp -o StrictHostKeyChecking=no target/*.war ec2-user@10.0.1.66:/optt/tomcat/apache-tomcat-8.5.68/webapps/ROOT'      }
    }
}
