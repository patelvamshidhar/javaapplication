pipeline {
    agent any
    
    stages {
        stage('Install npm') {
            steps {
                script {
                    docker.image('node:14').inside {
                        sh 'npm --version'
                    }
                }
            }
        }
        stage('Install Maven') {
            steps {
                script {
                    docker.image('maven:3.6.3-jdk-11').inside {
                        sh 'mvn --version'
                    }
                }
            }
        }
        stage('Build Java') {
            steps {
                script {
                    docker.image('maven:3.6.3-jdk-11').inside {
                        writeFile file: 'HelloWorld.java', text: '''
                        public class HelloWorld {
                            public static void main(String[] args) {
                                System.out.println("Hello, World!");
                            }
                        }
                        '''
                        sh 'javac HelloWorld.java'
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    docker.image('node:14').inside {
                        writeFile file: 'index.html', text: '''
                        <html>
                        <body>
                            <h1>Hello, World!</h1>
                        </body>
                        </html>
                        '''
                        sh 'npm install -g http-server'
                        sh 'http-server -p 8080'
                    }
                }
            }
        }
    }
}
