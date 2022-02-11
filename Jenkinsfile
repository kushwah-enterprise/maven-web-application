node{
    
    properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'JobLocalConfiguration', changeReasonComment: ''],
pipelineTriggers([pollSCM('* * * * *')])])
    
def mavenHome = tool name: "maven3.8.4"

stage('CheckoutCode'){

git branch: 'development', credentialsId: '7e4189ba-a101-45f9-9715-5c6a65bb9910', url: 'https://github.com/kushwah-enterprise/maven-web-application.git'

}

stage('Build'){

sh "${mavenHome}/bin/mvn clean package"
}
/*
//to generate sonarqube report
stage('ExecuteSonarQubeReport'){
sh "${mavenHome}/bin/mvn sonar:sonar"
}

//to upload artifacts to nexus repo
stage('UploadArtifactsIntoNexusRepo'){
sh "${mavenHome}/bin/mvn deploy"
}

//deploying application to tomcat server
stage('DeployAppintoTomcatServer'){

sshagent(['7920a0ac-afeb-4feb-a1df-b99a3010797c']) {
    sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@65.0.97.201:/opt/apache-tomcat-9.0.58/webapps/"
}


}
*/

}//node close
