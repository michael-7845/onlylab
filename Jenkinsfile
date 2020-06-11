pipeline {
    agent { docker 'maven:3.3.3' }
    stages {
        stage('build') {
            steps {
                sh 'mvn --version'
            }
        }
        stage('Build 2') {
             steps {
                 sh 'echo "Hello World"'
                 sh '''echo "Multiline shell steps works too"
                       ls -lah'''
             }
        }
        stage('Deploy') {
             steps {
                 sh 'chmod 755 ./flakey-deploy.sh'
                 retry(3) {
                      sh './flakey-deploy.sh'
                 }
             }
        }
    }
}