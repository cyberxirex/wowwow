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
                sh 'echo ${env.IMAGE_REPO}:${IMAGE_VERSION}'
      	        sh 'docker build . --tag ${env.IMAGE_REPO}:latest'
            }
        }
        stage('Docker Tagging') {
            agent any 
            steps {
                sh 'docker tag ${env.IMAGE_REPO}:latest ${env.IMAGE_REPO}:${IMAGE_VERSION}'
            }
        }
    }
}
