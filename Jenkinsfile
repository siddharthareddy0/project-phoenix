pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out code from GitHub'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Validating HTML file existence'
                bat '''
                if not exist education.html (
                    echo education.html NOT FOUND
                    exit /b 1
                )
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Running basic HTML validation'
                bat '''
                findstr /i "<html" education.html || exit /b 1
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying education.html (simulation)'
                echo 'HTML page deployed successfully'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully'
        }
        failure {
            echo 'Pipeline failed'
        }
    }
}
