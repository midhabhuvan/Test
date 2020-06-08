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
                withCredentials([usernamePassword( credentialsId: 'docker-hub-credentials', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    docker.withRegistry('', 'docker-hub-credentials') {
                            sh "docker login -u ${USERNAME} -p ${PASSWORD}"
                            dockerImage.push("${env.BUILD_NUMBER}")
                            dockerImage.push("latest")
                    }

                }   
            }    
         }
      }
      
   }
}

