pipeline{
   agent any
   tools { 
        maven 'Maven'
        'hudson.plugins.sonar.SonarRunnerInstallation' 'Sonar'
   }
   //tool name: 'Sonar', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
   stages('Developer')
   {
      stage('chekoutstage')
      {
         agent { label 'Agent1' }
         steps
         {
            checkout scm
         }
      }
  
   stage('Build')
      {
          agent { label 'Agent1' }
         steps
         {
            sh "mvn clean test"
         }
      }
      stage ('unit test')
      {
          agent { label 'Agent2' }
         steps
         {
            junit '**/target/**/*.xml'
         }
      }
      stage ( 'Sonar Analysis')
      {
          agent { label 'Agent1' }
         steps
         {
            sh "${tool 'Sonar'}/bin/sonar-scanner -Dsonar.host.url=http://sonarcloud.io -Dsonar.java.binaries=target/classes/ -Dsonar.login=82ae3896ef5c524cef63cd82906018ee31852f42 -Dsonar.projectName=ratna -Dsonar.projectVersion=3 -Dsonar.projectKey=march30th -Dsonar.sources=. -Dsonar.organization=march30th"
         }
      }
      
   }
}
