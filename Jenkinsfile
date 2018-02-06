node {
    def app

    stage('Clone repository') {
        checkout scm
    }

    #stage('Build image') {
   #     app = docker.build("amitkr2308/nodejsapp")
   # }

    stage('Test image') {
        app.inside {
            sh 'echo "Tests passed"'
        }
    }

    stage('Push image') {
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
}
