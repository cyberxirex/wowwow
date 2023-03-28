// 마지막 push image 스테이지의 버전을 변경하시오.
node {
   def IMAGE_VERSION = '1.0.0'
   stage('##### Clone repository') {
     checkout scm 
   }
   stage('### Build image') {
     app = docker.build("${env.IMAGE_REPO}")
   }
   stage('### Push image') {
         docker.withRegistry("https://registry.hub.docker.com/${env.IMAGE_REPO}", "dockerhub_credentials") {
            app.push(IMAGE_VERSION)
            app.push("latest")
         }
   }
}
