pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                sh "ls -a"
            }
        }
        stage('Build') {
            steps {
                    sh "docker build -f Dockerfile.bld -t irssibld ."
            }
        }
        stage('Archive') {
            steps {
                archiveArtifacts artifacts: '/irssi/Build/src/fe-text/irssi', allowEmptyArchive: false, fingerprint: true
            }
        }
        stage('Test') {
            steps {
                    sh "docker build -f Dockerfile.test -t irssitest ."
                
            }
        }
        stage('Deploy'){
            steps {
                    sh "docker build -f Dockerfile.dep -t irssidep ."   
                    sh "docker run -dit irssidep"
            }
        }
    }
}
