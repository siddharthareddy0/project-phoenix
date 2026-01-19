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
                sh '''
                  if [ ! -f education.html ]; then
                    echo "education.html NOT FOUND"
                    exit 1
                  fi
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Running basic HTML validation'
                sh '''
                  grep -i "<html" education.html || exit 1
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
