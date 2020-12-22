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
                    
                }
            }
        }
    }
}
