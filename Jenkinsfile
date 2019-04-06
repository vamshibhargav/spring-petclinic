pipeline{
   agent any
   tools { 
        maven 'Maven'
        'hudson.plugins.sonar.SonarRunnerInstallation' 'Sonar'
   }
   parameters {
    string(name: 'parameter1', description: 'dummykey')
    string(name: 'parameter2', description: 'dummykey')
  }
   //tool name: 'Sonar', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
   stages('Developer')
   {
      stage('chekoutstage')
      {
         steps
         {
            
            sh "echo ${parameter1}"
            checkout scm
         }
      }
  
   stage('Build')
      {
         steps
         {
            sh "mvn clean package"
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
            sh "${tool 'Sonar'}/bin/sonar-scanner -Dsonar.host.url=http://sonarcloud.io -Dsonar.java.binaries=target/classes/ -Dsonar.login=82ae3896ef5c524cef63cd82906018ee31852f42 -Dsonar.projectName=ratna -Dsonar.projectVersion=${parameter1} -Dsonar.projectKey=march30th -Dsonar.sources=. -Dsonar.organization=march30th"
         }
      }
      
      stage('Docker Build') {
      steps {
        sh '/usr/bin/docker build -t 173368197931.dkr.ecr.us-east-2.amazonaws.com/petclinc:latest .'
      }
    }
    stage('Push image') {
      steps {
        withDockerRegistry([credentialsId: '2d888c37-682f-4fc5-a73f-5e93c1356fd4', url: "https://173368197931.dkr.ecr.us-east-2.amazonaws.com/petclinc/"]) {
          sh '/usr/bin/docker push 173368197931.dkr.ecr.us-east-2.amazonaws.com/petclinc:latest'
        }
      }
    }
   }
}
