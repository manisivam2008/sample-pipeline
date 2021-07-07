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
         sh 'copy target/*.war /home/ubuntu'      
        }
    }
}
