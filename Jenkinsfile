pipeline {
    agent any
    stages {
        stage('Clone'){
            steps {
                git 'https://github.com/vitamingau/java-test.git'
            }
        }
        stage('ssh remote server') {
            steps {
                sshagent(['ssh-remote']) {
                    sh 'ssh -o StrictHostKeyChecking=no -l root 10.148.0.54 bin/build'
                }
            }
        }
    }
}
