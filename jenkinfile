pipeline {
    agent any

    stages {
        stage('Install npm') {
            steps {
                sh 'curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -'
                sh 'sudo apt-get install -y nodejs'
            }
        }
        stage('Install Maven') {
            steps {
                sh 'sudo apt-get update'
                sh 'sudo apt-get install -y maven'
            }
        }
        stage('Compile Java') {
            steps {
                sh 'javac HelloWorld.java'
            }
        }
        stage('Run Java') {
            steps {
                sh 'java HelloWorld'
            }
        }
        stage('Run npm') {
            steps {
                sh 'npm --version'
            }
        }
        stage('Run Maven') {
            steps {
                sh 'mvn --version'
            }
        }
    }
}
