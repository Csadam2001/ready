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
    }
}