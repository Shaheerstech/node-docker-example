pipeline {
    agent any

    environment {
        DOCKER_HUB_CREDENTIALS = credentials('shaheerahmed123') // You need to set up Docker Hub credentials in Jenkins
        GITHUB_REPO_URL = 'https://github.com/shaheerstech/https://github.com/Shaheerstech/node-docker-example.git'
        DOCKER_IMAGE_NAME = '$HOME/node_docker'
        DOCKER_IMAGE_TAG = "${env.BUILD_NUMBER}"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], userRemoteConfigs: [[url: "${env.GITHUB_REPO_URL}"]]])
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    def dockerImage = docker.build("${env.$HOME}:${env.node_docker}", "-f Dockerfile .")
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('', "${Shaheerahmed123}") {
                        dockerImage.push()
                    }
                }
            }
        }
    }

    post {
        success {
            echo 'Docker image built and pushed successfully.'
        }
        failure {
            echo 'Docker image build and/or push failed.'
        }
    }
}
