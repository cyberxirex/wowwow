node {
   stage('========== Clone repository ==========') {
     checkout scm
   }
   stage('========== Build image ==========') {
     app = docker.build("stepanowon/nodeapp-git")
   }
   stage('========== Push image ==========') {
      environment {
        IMAGE_VERSION = '1.0.0'
      }
      docker.withRegistry('https://registry.hub.docker.com/stepanowon/nodeapp-git', 'dockerhub_credentials') {
        app.push("${env.IMAGE_VERSION}")
        app.push("latest")
     }
   }
}
