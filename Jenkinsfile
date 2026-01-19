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
                echo 'Building the application'
                mvn clean compile
            }
        }

        stage('Test') {
            steps {
                echo 'Running unit tests'
                mvn test
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application (simulation)'
                echo "Deploy successful"
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
