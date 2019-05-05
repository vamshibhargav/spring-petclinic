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
  parallel
  {
   stage ('build')
    {
     steps
     {
      sh "mvn clean ${compilation}"
      sh 'sleep 60'
     }
    }
   stage ('example2')
   {
    agent {label 'JnlpTestNode'}
   steps
   {
    sh "echo ${parameter2}"
    sh "echo ${MYENVIRONMENT}"
    sh "echo ${WORKSPACE}"
    sh 'echo sudhakar'
    sh 'sleep 180'
   }
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
