pipeline {
    agent ( dockerfile true )
    stages {
        stage('Clone'){
            steps {
                git 'https://github.com/vitamingau/java-test.git'
            }
        }
        stage('docker hub'){
            steps {
                withDockerRegistry(credentialsId: 'docker-hub', url: 'https://index.docker.io/v1/') {
                    sh 'bin/build'
                    
                }
            }
        }
    }
}
