pipeline {
    agent any
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
        stage('Deploy') {
            steps {
                sh '''
                    sudo cp /home/ubuntu/git/hello-world-war/target/hello-world-war-1.0.0.war \
                       /opt/apache-tomcat-10.1.34/webapps/
                '''
            }
        }
    }
    post {
        success {
            emailext subject: "Build Success: ${env.JOB_NAME}", \
                     body: "The build was successful. Please find the details below:\n\nJob: ${env.JOB_NAME}\nBuild Number: ${env.BUILD_NUMBER}", \
                     recipientProviders: [[$class: 'DevelopersRecipientProvider']], \
                     to: 'sanjayhoysal03@gmail.com'
        }
        failure {
            emailext subject: "Build Failed: ${env.JOB_NAME}", \
                     body: "The build has failed. Please check the logs for details:\n\nJob: ${env.JOB_NAME}\nBuild Number: ${env.BUILD_NUMBER}", \
                     recipientProviders: [[$class: 'DevelopersRecipientProvider']], \
                     to: 'sanjayhoysal03@gmail.com'
        }
    }
}
