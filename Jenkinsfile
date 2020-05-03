pipeline
{
agent any
stages
{
stage('scm-checkout')
{
steps
{
git branch: 'master', url: 'https://github.com/Jaynath1992/maven-project'
}
}
stage('Maven compile')
{
steps
{
withMaven(jdk: 'localjdk-8', maven: 'localmaven') {
    sh 'mvn compile'
}
}
}
stage('Maven Test')
{
steps
{
withMaven(jdk: 'localjdk-8', maven: 'localmaven') {
    sh 'mvn test'
}
}
}
stage('Build my job')
{
steps
{
withMaven(jdk: 'localjdk-8', maven: 'localmaven') {
    sh 'mvn package'
}
}
}
stage('Deploy artifact to tomcat')
{
steps
{
sshagent(['deploytomcat']) {
    sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@3.21.236.18:/var/lib/tomcat/webapps'
}
}
}
}
}
