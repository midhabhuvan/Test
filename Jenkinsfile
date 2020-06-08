pipeline {
   agent {label 'staging'}
    environment {
      registry = "midhabhuvan/devops"
      registryCredential = 'docker-hub-credentials'
      dockerImage = ''
    }

   stages {
      stage('Download Git Code') {
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
                dockerImage = docker.build("learningimage")
                 }    
            }
        }
        stage('Publish Docker Image To Docker Hub') {
         steps {
            script{
               // Build Docker Image
                echo 'Publishing Image To DockerHUb'
                docker.withRegistry( '', registryCredential ) {
                    dockerImage.push()
                    }
                }
            }    
         }
      }
}
