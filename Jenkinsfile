pipeline {
    agent any

    stages {
        stage('Install dependencies') {
            steps {
                // Create a virtual environment and install dependencies
                sh 'python3 -m venv venv'
                sh './venv/bin/pip install -r requirements.txt'
            }
        }

        stage('Run tests') {
            steps {
                // Run pytest and generate a JUnit XML report
                sh './venv/bin/pytest --junitxml=report.xml'
            }
        }

        stage('Publish Report') {
            steps {
                // Publish the test results in Jenkins
                junit 'report.xml'
            }
        }
    }
}
