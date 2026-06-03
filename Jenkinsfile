pipeline {
    agent any

    environment {
        DOCKER_CREDS = credentials('05fc063d-4134-40be-967e-f69d1a218699')
    }

    stages {

        stage('clean workspace') {
            steps {
                deleteDir()
            }
        }

        stage('checkout') {
            steps {
                checkout scm
            }
        }

        stage('build docker image') {
            steps {
                sh 'docker build -t akshaya786/my-node-app:latest .'
            }
        }

        stage('login to docker hub') {
            steps {
                sh '''
                echo "$DOCKER_CREDS_PSW" | docker login -u "$DOCKER_CREDS_USR" --password-stdin
                '''
            }
        }

        stage('push image') {
            steps {
                sh 'docker push akshaya786/my-node-app:latest'
            }
        }
    }
}