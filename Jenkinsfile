pipeline {
    agent any

    environment {
        EMAIL_RECIPIENT = 'your-email@gmail.com'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/your-username/html-css-jenkins-demo.git'
            }
        }

        stage('Archive HTML/CSS') {
            steps {
                archiveArtifacts artifacts: '**/*.html, **/*.css', fingerprint: true
            }
        }
    }

    post {
        success {
            mail to: "${EMAIL_RECIPIENT}",
                 subject: "✅ Build Success: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                 body: "Your HTML/CSS project built successfully."
        }
        failure {
            mail to: "${EMAIL_RECIPIENT}",
                 subject: "❌ Build Failed: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                 body: "The build failed. Please check Jenkins logs."
        }
    }
}
