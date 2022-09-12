pipeline {
    agent any
    triggers {
        pollSCM '* * * * *'
    }
    stages {
        stage('Build gradle') {
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
                bat 'docker run -p 8081:8080 myorg/myapp'
            }
        }
    }
}