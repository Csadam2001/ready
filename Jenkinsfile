pipeline {
    agent any
    triggers {
        pollSCM '* * * * *'
    }
    stages {
        stage('Build gradle') {
            steps {
                bat './gradlew build'
            }
        }
        stage('Build docker') {
            steps {
                bat 'docker build --build-arg JAR_FILE=build/libs/demo-0.0.1-SNAPSHOT.jar -t app .'
            }
        }
        stage('Run docker') {
            steps {
                bat 'docker run -p 8081:8081 app'
            }
        }
    }
}