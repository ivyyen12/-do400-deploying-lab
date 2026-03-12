pipeline {
    agent { label 'maven' }

    stages {
        stage('Test') {
            steps {
                sh './mvnw verify'
            }
        }
    }
}



