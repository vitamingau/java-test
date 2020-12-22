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
                    sh 'chmod +x bin/build'
                    sh 'bin/build'
                    sh 'docker push phuphan/java-test'
                }
            }
        }
        stage('ssh remote server') {
            steps {
                sshagent(['ssh-remote']) {
                    sh 'ssh -o StrictHostKeyChecking=no -l root 35.240.166.66 docker run -d --name java-test -p 8080:8080 phuphan/java-test'                 
                }
            }
        }
    }
}
