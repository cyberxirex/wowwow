node {
  environment {
    IMAGE_VERSION = '1.0.1'
  }
  stage('========== Clone repository ==========') {
    checkout scm
  }
  stage('========== Build image ==========') {
    app = docker.build("stepanowon/nodeapp-git")
    echo "VERSION : ${env.IMAGE_VERSION}"
  }
  stage('========== Push image ==========') {
    docker.withRegistry('https://registry.hub.docker.com/stepanowon/nodeapp-git', 'dockerhub_credentials') {
      app.push("${env.IMAGE_VERSION}")
      app.push("latest")
    }
  }
}
