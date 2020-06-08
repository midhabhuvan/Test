pipeline {
   agent {label 'staging'}

   stages {
      stage('Download') {
         steps {
            // Get some code from a GitHub repository
            git 'https://github.com/midhabhuvan/Test.git'
         }
      }
      stage('Build Docker Image') {
         steps {
            // Get some code from a GitHub repository
            echo 'Starting to build docker image'
         }
      }
      
   }
}
