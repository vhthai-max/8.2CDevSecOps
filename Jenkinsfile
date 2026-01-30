pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test || true'
            }
        }

        stage('Security Scan - npm audit') {
            steps {
                sh 'npm audit || true'
            }
        }
    }
}
post {
    always {
        emailext (
            subject: "Build Result: ${currentBuild.currentResult}",
            body: "Build finished with status: ${currentBuild.currentResult}",
            to: "yourgmail@gmail.com",
            attachLog: true
        )
    }
}
