// 마지막 push image 스테이지의 버전을 변경하시오.
node {
   stage('========== Clone repository ==========') {
     checkout scm
   }
   stage('========== Build image ==========') {
     app = docker.build("stepanowon/nodeapp-git")
   }
   stage('========== Push image ==========') {
      withEnv(["IMAGE_VERSION=1.0.2"]) {
         docker.withRegistry('https://registry.hub.docker.com/stepanowon/nodeapp-git', 'dockerhub_credentials') {
            app.push("${env.IMAGE_VERSION}")
            app.push("latest")
         }
      }
   }
}
