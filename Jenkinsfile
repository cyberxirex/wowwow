pipeline {
   agent any
   environment {
       IMAGE_VERSION = '1.0.1'
   }
   stages {
     stage('###Clone Repository') {
       steps {
         checkout scm
       }
     }
     stage('###Build image') {
       steps { 
         app = docker.build("stepanowon/nodeapp-git")
         echo "VERSION : ${env.IMAGE_VERSION}"
       }
     }
     stage('###Push image') {
       steps {
         docker.withRegistry('https://registry.hub.docker.com/stepanowon/nodeapp-git', 'dockerhub_credentials') {
           app.push("${env.IMAGE_VERSION}")
           app.push("latest")
         }
       }
     }
   }
}
