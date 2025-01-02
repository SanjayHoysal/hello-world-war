pipeline {
    agent { label 'Slave1' }
    parameters {
        string(name: 'cmd', defaultValue: 'package', description: 'Maven command to run')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
    }
    stages {
        stage('Checkout') {
            steps {
                sh 'rm -rf hello-world-war'
                sh 'git clone https://github.com/SanjayHoysal/hello-world-war.git'
            }
        }
        stage('Build') {
            steps {
                sh '''
                    cd hello-world-war
                    mvn clean ${cmd}
                '''
            }
        }
    }
}
