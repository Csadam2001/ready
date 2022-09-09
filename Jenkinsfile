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
        stage('Run docker image'){
            steps{
                bat ''
            }
        }
    }
 }