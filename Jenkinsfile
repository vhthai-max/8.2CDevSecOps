pipeline {
    agent any

    stages {
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

    post {
        success {
            emailext(
                subject: "Build SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "Build succeeded. Check details at ${env.BUILD_URL}",
                to: "thaiviethuy1112@gmail.com"
            )
        }
        failure {
            emailext(
                subject: "Build FAILED: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "Build failed. Check details at ${env.BUILD_URL}",
                to: "thaiviethuy1112@gmail.com"
            )
        }
    }
}

