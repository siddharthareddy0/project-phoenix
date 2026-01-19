pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out source code'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Build validation: file existence'
                bat '''
                if not exist Page\\education.html (
                    echo ERROR: education.html not found
                    exit /b 1
                )
                '''
            }
        }

        stage('QA - HTML Structure') {
            steps {
                echo 'Running HTML quality checks'
                bat '''
                findstr /i "<html" Page\\education.html || exit /b 1
                findstr /i "<head" Page\\education.html || exit /b 1
                findstr /i "<body" Page\\education.html || exit /b 1
                findstr /i "<title" Page\\education.html || exit /b 1
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying HTML page (simulation)'
                echo 'Deployment successful'
            }
        }
    }

    post {
        success {
            echo 'QUALITY GATE PASSED – Pipeline successful'
        }
        failure {
            echo 'QUALITY GATE FAILED – Fix issues before deploy'
        }
    }
}
