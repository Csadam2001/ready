pipeline {
    agent any
    triggers {
        pollSCM '* * * * *'
    }
    stages {
        stage('Build docker') {
            steps {
                bat './gradlew bootRun --args=--server.port=8081'
            }
        }
       /* stage('Run docker') {
            steps {
                bat 'docker run -p 8081:8081 myorg/myapp'
            }
        }*/
    }
}