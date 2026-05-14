agent {
    docker { image 'python:3.11-slim' }
}

pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Getting the code...'
                checkout scm
            }
        }

        stage('Install dependencies') {
            steps {
                echo 'Installing pytest...'
                sh 'pip install pytest --break-system-packages || pip install pytest'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'python -m pytest test_app.py -v'
            }
        }

        stage('Done') {
            steps {
                echo 'All good! 🎉'
            }
        }
    }

    post {
        success {
            echo 'Pipeline succeeded.'
        }
        failure {
            echo 'Pipeline failed. Check the logs.'
        }
    }
}
