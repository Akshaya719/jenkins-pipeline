pipeline {
    agent any

    environment {
        DOCKER_CREDS = credentials('05fc063d-4134-40be-967e-f69d1a218699')
    }

    stages {
        // Option 1: Clean the workspace safely using cleanWs()
        stage('clean workspace') {
            steps {
                cleanWs() 
            }
        }

        // Option 2: Manual checkout is optional, but if you keep it, 
        // it will now work perfectly because .git structure isn't broken
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
    
    // Pro-Tip: Clean up the workspace after the build finishes (success or failure)
    post {
        always {
            cleanWs()
        }
    }
}