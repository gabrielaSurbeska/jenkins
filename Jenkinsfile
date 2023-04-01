pipeline {
    agent any

    stages {
        stage('Clone repository') {
        checkout scm
    }
    stage('Build image') {
       app = docker.build("gabrielasurbeska/jenkins")
    }
    stage('Push image') {   
        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
	@@ -13,4 +15,5 @@ node {
            // signal the orchestrator that there is a new version
        }
    }
  }
}
