def IMAGE_VERSION = '1.0.0'
pipeline {
	agent any
	stages {
  		stage("Checkout") {
			steps {
				checkout scm
			}
		}
        stage('Docker Build') {
            agent any
            steps {
                echo "${env.IMAGE_REPO}:${IMAGE_VERSION}"
                app = docker.build("${env.IMAGE_REPO}")
            }
        }
    }
}
