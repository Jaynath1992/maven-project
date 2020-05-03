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
}
}
