node {
  stage('========== Clone repository ==========') {
    checkout scm
  }
  stage('========== Build image ==========') {
    app = docker.build("stepanowon/nodeapp-git")
    steps {
       sh 'VERSION=$(head -n 1 Dockerfile | sed 's/#//' | sed 's/\r//')'
    }
  }
  stage('========== Push image ==========') {
    docker.withRegistry('https://registry.hub.docker.com/stepanowon/nodeapp-git', 'dockerhub_credentials') {
      app.push("${env.VERSION}")
      app.push("latest")
    }
  }
}
