pipeline {
    agent any
    stages {
        stage('Hello') {
            steps {
                script {
                    sh 'echo hello'
                }
            }
        }
        stage('Hello docker') {
            steps {
                script {
                    sh 'docker run hello-world'
                }
            }
        }
    }
}