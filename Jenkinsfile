```groovy
pipeline {
    agent any

    triggers {
        cron('H/2 * * * *')
    }

    options {
        skipDefaultCheckout(true)
        timeout(time: 5, unit: 'MINUTES')
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Preparing Python application'
                sh 'python3 --version'
            }
        }

        stage('Test') {
            steps {
                sh 'python3 app.py'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check the console output.'
        }
        aborted {
            echo 'Pipeline was aborted or timed out.'
        }
    }
}
```