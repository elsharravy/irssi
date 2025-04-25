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
                dir("irssi") { 
                    sh "ls -a"
                    sh "pwd"
                    sh "docker build -f Dockerfile.bld -t build ."
                }
            }
        }
        stage('Test') {
            steps {
                dir("irssi") { 
                    sh "ls -a"
                    sh "pwd"
                    sh "docker build -f Dockerfile.test -t test ."
                }
            }
        }
    }
}
