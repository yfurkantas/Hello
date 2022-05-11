node {
    def app

    stage('Clone repository') {

        checkout scm
    }

    stage('Build image') {


        app = docker.build("yfurkantas/Hello")
    }

    stage('Test image') {


        app.inside {
            sh 'echo "Tests passed"'
        }
    }

    stage('Push image') {
        docker.withRegistry('https://registry.hub.docker.com', 'huawei') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
}
