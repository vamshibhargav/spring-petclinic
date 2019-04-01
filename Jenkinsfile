pipeline{
   agent any
   tools { 
        maven 'Maven'
   }
   stages('Checkout')
   {
      stage('chekoutstage')
      {
         steps
         {
            checkout scm
         }
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
}
