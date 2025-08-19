pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
               git branch: 'main', url: 'https://github.com/dangerthe/simple-py-app.git'
            }
        }
        stage('Install') {
            steps {
             bat 'python -m venv venv'
             bat 'venv\\Scripts\\Activate.ps1; pip install -r requirements.txt'
             bat 'venv\\Scripts\\Activate.ps1; python -m unittest discover'
            }
        }
        stage('Test') {
            steps {
            bat 'venv\\Scripts\\Activate.ps1; python -m unittest discover'
            }
        }
        stage('Run') {
            steps {
                bat 'venv\\Scripts\\Activate.ps1; python app.py'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying app...'
                // Add deployment steps here (e.g., copy files, restart server)
            }
        }
    }

    post {
        success {
            echo 'Build, test, and deploy succeeded!'
        }
        failure {
            echo 'Something went wrong in the pipeline.'
        }
    }
}
