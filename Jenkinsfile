pipeline {
     parameters {
        string(name: 'cmd', defaultValue: 'package', description: 'Who should I say hello to?')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
    agent any
      stages {
        stage('checkout') {
            steps {
                sh 'rm -rf hello-world-war'
                sh 'git clone https://github.com/SanjayHoysal/hello-world-war.git'
            }
        }
        stage('build') {
            steps {
                sh 'cd hello-world-war'
                sh 'mvn clean $cmd'
            }
        }
    }
}
