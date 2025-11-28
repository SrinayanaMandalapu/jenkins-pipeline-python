pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo '🔹 Checking out source code...'
                git branch: 'main', url: 'https://github.com/SrinayanaMandalapu/jenkins-pipeline-python.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo '🔹 Installing dependencies using pip...'
                bat 'pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                echo '🔹 Running pytest...'
                bat 'pip install pytest'
                bat 'pytest test_app.py'
            }
        }

        stage('Archive Artifacts') {
            steps {
                echo '🔹 Archiving build artifacts...'
                archiveArtifacts artifacts: '**/*.py', fingerprint: true
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline executed successfully!'
        }
        failure {
            echo '❌ Pipeline failed. Check console output for details.'
        }
    }
}
