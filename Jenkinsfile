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
        stage('Archive') {
            steps {
                sh "docker cp $(docker ps -q --filter ancestor=irssidep):/usr/local/bin/irssi "${WORKSPACE}"/irssi"
                archiveArtifacts artifacts: 'irssi', allowEmptyArchive: false, fingerprint: true
                
                //archiveArtifacts artifacts: '/irssi/Build/src/fe-text/irssi', allowEmptyArchive: false, fingerprint: true
                //archiveArtifacts artifacts: 'irssidep:/usr/local/bin/irssi', allowEmptyArchive: false, fingerprint: true


            }
        }
    }
}
