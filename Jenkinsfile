pipeline{
 agent any
 tools { 
        maven 'Maven'
        'hudson.plugins.sonar.SonarRunnerInstallation' 'Sonar'
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
        sh "mvn clean package"
     }
    }
   stage ('example2')
   {
    agent {label 'JnlpTestNode'}
   steps
   {
      sh 'echo sudhakar2'
   }
   }
 }
}
