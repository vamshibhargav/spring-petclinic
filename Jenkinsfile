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
    agent {label 'JnlpTestNode'}
   steps
   {
    sh "echo ${paramenter2}"
    sh 'echo sudhakar'
   }
   }
 }
}
