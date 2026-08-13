pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Starting Build...'
                echo 'Application build completed successfully.'
            }
        }

        stage('Test') {
            steps {
                echo 'Starting Tests...'
                echo 'All tests passed successfully.'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Starting Deployment...'
                echo 'Application deployed successfully.'
            }
        }
    }

    post {
        success {
            echo 'CI/CD Pipeline completed successfully!'
        }

        failure {
            echo 'CI/CD Pipeline failed.'
        }
    }
}
