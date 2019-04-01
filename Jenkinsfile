pipeline{
   agent any
    def mvnHome= tool 'Maven'
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
   stages('Build')
   {
      stage('Build')
      {
         steps
         {
            sh "${mvnHome}/bin/mvn clean test"
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
}
