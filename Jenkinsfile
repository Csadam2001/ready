pipeline {
    agent any
    triggers {
        pollSCM '* * * * *'
    }
    stages {
        stage('Build') {
            steps {
                bat './gradlew assemble'
            }
        }
        stage('Test') {
            steps {
                bat './gradlew test'
            }
        }
        stage('Build Docker image') {
            steps {
                bat './gradlew docker'
            }
        }
        stage('Push Docker image') {
            environment {
                DOCKER_HUB_LOGIN = credentials('docker-hub')
            }
            steps {
                bat 'docker login --username=$DOCKER_HUB_LOGIN_USR --password=$DOCKER_HUB_LOGIN_PSW'
                bat './gradlew dockerPush'
            }
        }
    }
}