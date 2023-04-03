node {
    def app
    stage('Clone repository') {
        checkout scm
    }
    stage('Build image') {
       app = docker.build("gabrielasurbeska/jenkinss")
    }
    stage('Push image') {   
        docker.withRegistry('https://login.docker.com/u/login/identifier?state=hKFo2SBzdVlkRzBudEtnZklPV0dpYXRZaXdWQWVvdjI4Tk1qLaFur3VuaXZlcnNhbC1sb2dpbqN0aWTZIEd1aDRueE1pWmgyS2tYRkllOW5KSEo3WnhXLXVYb2Uxo2NpZNkgbHZlOUdHbDhKdFNVcm5lUTFFVnVDMGxiakhkaTluYjk', 'dockerhub') {
            app.push("${env.BRANCH_NAME}-${env.BUILD_NUMBER}")
            app.push("${env.BRANCH_NAME}-latest")
            // signal the orchestrator that there is a new version
        }
    }
}
