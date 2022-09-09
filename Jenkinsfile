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
                bat 'docker build --build-arg JAR_FILE=build/libs/*.jar -t myorg/myapp .'
            }
        }
        stage('Run docker') {
            steps {
                bat 'docker run -p 9090:8080 myorg/myapp'
            }
        }
    }
}