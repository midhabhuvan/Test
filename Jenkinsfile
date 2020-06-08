pipeline {
   agent {label 'staging'}
    environment {
      registry = "midhabhuvan/devops"
      registryCredential = 'docker-hub-credentials'
      dockerImage = ''
    }
   def version 
   def versions 
   def major
   def minor
   def patch
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
                dockerImage = docker.build(registry + ":latest")
                 }    
            }
        }

      stage('Publish Docker Image To Docker Hub') {
         steps {
            script{
               // Build Docker Image
                echo 'Publishing Image To DockerHUb'
                version = readFile('VERSION')
                versions = version.split('\\.')
                major = versions[0]
                minor = versions[0] + '.' + versions[1]
                patch = version.trim()
                docker.withRegistry( '', registryCredential ) {
                   dockerImage.push()
                   dockerImage.push(major)
                   dockerImage.push(minor)
                   dockerImage.push(patch)
                   
                 } 
  
            }    
         }
      }
      
   }
}

