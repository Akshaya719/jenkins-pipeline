// pipeline {
//     agent any

//     // This stops Jenkins from doing the broken automatic checkout at the start
//     options {
//         skipDefaultCheckout()
//     }

//     environment {
//         DOCKER_CREDS = credentials('05fc063d-4134-40be-967e-f69d1a218699')
//     }

//     stages {
//         stage('Initialize & Clean') {
//             steps {
//                 // Clean the workspace safely before getting code
//                 cleanWs()
                
//                 // Manually pull the code now that the workspace is fresh
//                 checkout scm
//             }
//         }

//         stage('build docker image') {
//             steps {
//                 sh 'docker build -t akshaya786/my-node-app:latest .'
//             }
//         }

//         stage('login to docker hub') {
//             steps {
//                 sh '''
//                 echo "$DOCKER_CREDS_PSW" | docker login -u "$DOCKER_CREDS_USR" --password-stdin
//                 '''
//             }
//         }

//         stage('push image') {
//             steps {
//                 sh 'docker push akshaya786/my-node-app:latest'
//             }
//         }
//     }
// }
pipeline{
    agent any
    stages{
        stage('checkout code'){
            
            steps{
                checkout scm
            }
        }
        stage('build docker image'){
            steps{
                sh 'docker build -t myapp:latest .'
            }
        }
    }
}