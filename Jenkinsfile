pipeline {
    agent any
    tools {
        maven 'Maven_3.9.7' // Ensure the name matches the configured Maven installation in Jenkins
    }
    environment {
        PATH = "${tool 'Maven_3.9.7'}/bin:${env.PATH}"
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Blaundos/sample-project.git'
            }
        }
        stage('Compile') {
            steps {
                sh 'mvn compile'
            }
        }
        stage('Code Review') {
            steps {
                sh 'mvn checkstyle:check'
            }
        }
        stage('Unit Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }
        stage('Deploy to Local Tomcat') {
            steps {
                sh '''
                cp target/my-web-app.war ~/tomcat/webapps/
                '''
            }
        }
    }
}
