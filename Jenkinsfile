pipeline {
    agent any
    triggers {
        pollSCM '* * * * *'
    }
    stages {
        stage('Build') {
            steps {
                bat './gradlew bootRun'
            }
        }
        stage('Build docker') {
            steps {
                bat 'docker build --build-arg JAR_FILE=build/libs/*.jar -t myorg/myapp .'
            }
        }
        stage('Run docker') {
            steps {
                bat 'docker run -p 8081:8081 myorg/myapp'
            }
        }
    }
}