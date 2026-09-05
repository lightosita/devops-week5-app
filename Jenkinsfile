pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building application...'
                sh 'python3 -m py_compile app.py'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'pthon3 app.py'
            }
        }

        stage('Validation') {
            steps {
                echo 'Running validation...'
                sh 'test -f app.py'
                sh 'test -f Jenkinsfile'
                echo 'Validation passed!'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }

        failure {
            echo 'Pipeline failed. Check the Console Output.'
        }
    }
}
