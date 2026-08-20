pipeline {

    agent any

    environment {
        S3_BUCKET = 'YOUR_BUCKET_NAME'
    }

    triggers {
        githubPush()
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }


        stage('Install Dependencies') {
            steps {
                sh '''
                python3 -m venv venv
                . venv/bin/activate
                pip install -r requirements.txt
                '''
            }
        }


        stage('Lint') {
            steps {
                sh '''
                . venv/bin/activate
                flake8 app.py test_app.py
                '''
            }
        }


        stage('Test') {
            steps {
                sh '''
                . venv/bin/activate
                pytest -v
                '''
            }
        }


        stage('Package') {
            steps {
                sh '''
                mkdir -p dist
                tar -czf dist/app-${BUILD_NUMBER}.tar.gz \
                app.py test_app.py requirements.txt
                '''
            }
        }


        stage('Upload to S3') {
            steps {
                sh '''
                aws s3 cp \
                dist/app-${BUILD_NUMBER}.tar.gz \
                s3://${S3_BUCKET}/
                '''
            }
        }
    }
}
