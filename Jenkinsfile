pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    def dockerImage = docker.build("shaheerahmed123/jenkins/jenkins:latest")
                    dockerImage.push()
                }
            }
        }
    }
}
