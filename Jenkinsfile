pipeline {
    agent any // You can use "any" agent type here

    stages {
        stage('Build and Push Docker Image') {
            agent {
                docker {
                    image 'jenkins/jenkins:latest'
                    args '-v /var/run/docker.sock:/var/run/docker.sock'
                }
            }
            steps {
                script {
                    // Build Docker image
                    def dockerImage = docker.build("shaheerahmed123/jenkins/jenkins:latest")

                    // Push Docker image
                    dockerImage.push()

                    // Additional step: Tag and push the image with a custom tag
                    def customTag = dockerImage.push("shaheerahmed123/jenkins/jenkins:custom-tag")
                }
            }
        }
    }
}
