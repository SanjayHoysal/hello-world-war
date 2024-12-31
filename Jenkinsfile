pipeline {
     parameters {
        string(name: 'PERSON', defaultValue: 'Package', description: 'Who should I say hello to?')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
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
                sh 'mvn clean $cmd'
            }
        }
    }
}
