pipeline{
 agent any
 tools { 
        maven 'Maven'
        'hudson.plugins.sonar.SonarRunnerInstallation' 'Sonar'
   }
  parameters {
    string(name: 'compilation', description: 'dummykey')
    string(name: 'parameter2', description: 'dummykey')
  }
 environment
 {
   MYENVIRONMENT="Sudhakar"
 }
 stages ('BuildStage')
 {
   stage ('Checkout')
   {
   steps
   {
      checkout scm
   }
   }
   stage ('build')
    {
     steps
     {
      sh "mvn clean ${compilation}"
     }
    }
   stage ('example2')
   {
   steps
   {
    sh "echo ${parameter2}"
    sh "echo ${MYENVIRONMENT}"
    sh "echo ${WORKSPACE}"
    sh 'echo sudhakar'
   }
   }
 }
 post
 {
   always
   {
      junit '**/target/**/*.xml'
   }
 }
}
