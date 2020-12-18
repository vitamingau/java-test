pipeline {
    agent any
    stages {
        stage('Clone'){
            steps {
                git 'https://github.com/vitamingau/java-test.git'
            }
        }
        stage('docker hub'){
            steps {
                withDockerRegistry(credentialsId: 'docker-hub', url: 'https://index.docker.io/v1/') {
                    sh 'docker build -t phuphan/java-test:v10 .'
                    sh 'docker push phuphan/java-test:v10'
                }
            }
        }
        stage('ssh remote server') {
            steps {
                sshagent(['ssh-remote']) {
                    sh 'ssh -o StrictHostKeyChecking=no -l root 35.240.166.66 bin/build'
                }
            }
        }
    }
}