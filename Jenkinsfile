pipeline {
    agent any
    options {
        buildDiscarder(logRotator(numToKeepStr: '5'))
    }
    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub')
        IMAGE_NAME = 'node'
    }
    stages {
        stage('Build') {
            steps {
                sh 'docker build -t ${env.node} .'
            }
        }
        stage('Login') {
            steps {
                sh "echo \$DOCKERHUB_CREDENTIALS_PSW | docker login -u \$DOCKERHUB_CREDENTIALS_USR --password-stdin"
            }
        }
        stage('Push') {
            steps {
                sh "docker push ${env.node}"
            }
        }
    }
    post {
        always {
            sh 'docker logout'
        }
    }
}
