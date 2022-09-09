pipeline {
    agent any
    triggers {
        pollSCM '* * * * *'
    }
    stages {
        stage('Build docker') {
            steps {
                bat './gradlew bootRun'
            }
        }
       /* stage('Run docker') {
            steps {
                bat 'docker run -p 8081:8081 myorg/myapp'
            }
        }*/
    }
}