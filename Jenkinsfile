node {
    def app
    stage('Clone repository') {
        checkout scm
    }
    stage('Build image') {
       app = docker.build("gabrielasurbeska/jenkinss")
    }
    stage('Push image') {
       withCredentials([usernamePassword( credentialsId: 'docker-hub-credentials', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
       docker.withRegistry('', 'docker-hub-credentials') {
       sh "docker login -u ${USERNAME} -p ${PASSWORD}"
       myImage.push("${env.BUILD_NUMBER}")
       myImage.push("latest")
       }
    }
}
