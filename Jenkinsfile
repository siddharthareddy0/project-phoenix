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
                  if [ ! -f Page/education.html ]; then
                    echo "education.html NOT FOUND in Page folder"
                    exit 1
                  fi
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Running basic HTML validation'
                sh '''
                  grep -i "<html" Page/education.html || exit 1
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying Page folder (simulation)'
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
