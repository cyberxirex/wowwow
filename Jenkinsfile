node {
  stage('========== Clone repository ==========') {
    checkout scm
  }
  stage('========== Build image ==========') {
    app = docker.build("stepanowon/nodeapp-git")
  }
  stage('========== Push image ==========') {
    docker.withRegistry('registry.hub.docker.com/stepanowon/nodeapp-git', 'dockerhub_credentials') {
      app.push("${env.BUILD_NUMBER}")
      app.push("latest")
    }
  }
}
