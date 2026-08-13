pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Starting Build...'
                sh 'python3 --version'
                sh 'python3 -m py_compile app.py'
                echo 'Build completed successfully.'
            }
        }

        stage('Test') {
            steps {
                echo 'Starting Tests...'
                sh 'python3 -m pytest test_app.py'
                echo 'Tests completed successfully.'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Starting Deployment...'
                sh 'mkdir -p deploy'
                sh 'cp app.py deploy/'
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
