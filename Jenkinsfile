node {
   stage('========== Clone repository ==========') {
     checkout scm
   }
   stage('========== Build image ==========') {
     app = docker.build("stepanowon/nodeapp-git")
   }
   stage('========== Push image ==========') {
      docker.withRegistry('https://registry.hub.docker.com/stepanowon/nodeapp-git', 'dockerhub_credentials') {
        environment {
          IMAGE_VERSION = '1.0.0'
        }
         echo "${env.IMAGE_VERSION}"
        app.push("${env.IMAGE_VERSION}")
        app.push("latest")
     }
   }
}
