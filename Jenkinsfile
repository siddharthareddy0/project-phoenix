pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out source code from GitHub'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Checking if education.html exists'
                bat '''
                if not exist Page\\education.html (
                    echo education.html NOT FOUND
                    exit /b 1
                )
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Validating HTML structure'
                bat '''
                findstr /i "<html" Page\\education.html || exit /b 1
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
