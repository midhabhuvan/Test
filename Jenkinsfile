pipeline {
   agent {label 'staging'}
    environment {
      registry = "midhabhuvan/devops"
      registryCredential = 'docker-hub-credentials'
      dockerImage = ''
  }

   stages {
      stage('Download') {
         steps {
            // Get some code from a GitHub repository
            git 'https://github.com/midhabhuvan/Test.git'
         }
      }
      stage('Build Docker Image') {
         steps {
            script{
               // Build Docker Image
                echo 'Starting to build docker image'
                dockerImage = sudo docker.build("FirstImage" + ":$BUILD_NUMBER")
            }
            
            
         }
      }
      
   }
}
