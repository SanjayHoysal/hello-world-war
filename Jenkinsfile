pipeline {
    agent any
      stages {
        stage('checkout') {
            steps {
                sh 'git clone https://github.com/SanjayHoysal/hello-world-war.git'
            }
        }
        stage('build') {
            steps {
                sh 'cd hello-world-war'
                sh 'mvn clean package'
            }
        }
    }
}
