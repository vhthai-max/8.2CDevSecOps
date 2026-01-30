pipeline {
  agent any

  stages {
    stage('Install Dependencies') {
      steps { sh 'npm install' }
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
    always {
      emailext(
        subject: "Jenkins Build: ${env.JOB_NAME} #${env.BUILD_NUMBER} - ${currentBuild.currentResult}",
        body: "Build result: ${currentBuild.currentResult}\nConsole: ${env.BUILD_URL}",
        to: "thaiviethuy1112@gmail.com"
      )
    }
  }
}
