pipeline {
    agent {
        node { label "maven" }
    }

    environment {
        QUAY = credentials('QUAY_USER')
    }

    stages {
        stage("Test") {
            steps {
                sh "./mvnw verify"
            }
        }

        stage("Build & Push Image") {
            steps {
                sh """
                    podman login -u $QUAY_USR -p $QUAY_PSW quay.io
                    podman build -t quay.io/$QUAY_USR/deploying-lab:latest .
                    podman push quay.io/$QUAY_USR/deploying-lab:latest
                """
            }
        }
    }
}



