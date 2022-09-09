pipeline {
    agent any
    triggers {
        pollSCM '* * * * *'
    }
    stages {
        stage('Build') {
            steps {
                bet './gradlew assemble'
            }
        }
        stage('Test') {
            steps {
                bet './gradlew test'
            }
        }
        stage('Build Docker image') {
            steps {
                bet './gradlew docker'
            }
        }
        stage('Push Docker image') {
            environment {
                DOCKER_HUB_LOGIN = credentials('docker-hub')
            }
            steps {
                bet 'docker login --username=$DOCKER_HUB_LOGIN_USR --password=$DOCKER_HUB_LOGIN_PSW'
                bet './gradlew dockerPush'
            }
        }
    