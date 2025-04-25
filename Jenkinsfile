pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                sh "ls -a"
                //sh "rm -rf irssi"
                //sh "git clone https://github.com/elsharravy/irssi.git"
            }
        }
        stage('Build') {
            steps {
                    sh "ls -a"
                    sh "pwd"
                    sh "docker build -f Dockerfile.bld -t irssibld ."
            }
        }
        stage('Test') {
            steps {
                    sh "ls -a"
                    sh "pwd"
                    sh "docker build -f Dockerfile.test -t irssitest ."
                
            }
        }
    }
}
