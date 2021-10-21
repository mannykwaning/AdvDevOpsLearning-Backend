pipeline {
    agent any 
    environment {
        registryCredential = 'docker'
        imageName = 'mannyaboah/nodebackend'
        dockerImage = ''
        }
    stages {
        
        stage('Run the tests') {
             agent {
                docker { 
                    image 'node:14-alpine'
                    args '-e HOME=/tmp -e NPM_CONFIG_PREFIX=/tmp/.npm'
                    reuseNode true
                }
            }
            steps {
                echo 'Retrieving source code from github'
                git branch: 'main',
                    url: 'https://github.com/mannyaboah/AdvDevOpsLearning-Backend.git'
                echo 'Did this work?'
                sh 'ls -a'
                
                // install dependencies
                sh 'npm install'
                
                // testing node app
                sh 'npm test' 
            }
        }
        // stage('Building image') {
        //     steps{
        //         script {
        //             echo 'build the image' 
        //         }
        //     }
        //     }
        // stage('Push Image') {
        //     steps{
        //         script {
        //             echo 'push the image to docker hub' 
        //         }
        //     }
        // }     
        //  stage('deploy to k8s') {
        //      agent {
        //         docker { 
        //             image 'google/cloud-sdk:latest'
        //             args '-e HOME=/tmp'
        //             reuseNode true
        //                 }
        //             }
        //     steps {
        //      }
        // }     
        // stage('Remove local docker image') {
        //     steps{
        //         sh "docker rmi $imageName:latest"
        //         sh "docker rmi $imageName:$BUILD_NUMBER"
        //     }
        // }
    }
}