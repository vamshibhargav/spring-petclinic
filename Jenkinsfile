pipeline{
   agent any
   tools { 
        maven 'Maven'
        sonar 'Sonar'
   }
   stages('Developer')
   {
      stage('chekoutstage')
      {
         steps
         {
            checkout scm
         }
      }
  
   stage('Build')
      {
         steps
         {
            sh "mvn clean test"
         }
      }
      stage ('unit test')
      {
         steps
         {
            junit '**/target/**/*.xml'
         }
      }
      stage ( 'Sonar Analysis')
      {
         steps
         {
             sh "sonar-scanner -Dsonar.host.url=http://sonarcloud.io -Dsonar.java.binaries=target/classes/ -Dsonar.login=82ae3896ef5c524cef63cd82906018ee31852f42 -Dsonar.projectName=ratna -Dsonar.projectVersion=3 -Dsonar.projectKey=march30th -Dsonar.sources=. -Dsonar.organization=march30th"
         }
      }
      
   }
}
