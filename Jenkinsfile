pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/thuytienngo/8.2CDevSecOps.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test || true'
            }
        }

        stage('Generate Coverage') {
            steps {
                sh 'npm run coverage || true'
            }
        }

        stage('Security Scan - npm audit') {
            steps {
                sh 'npm audit --json || true'
            }
        }
    }

    post {
        always {
            echo 'Pipeline completed. Check logs for npm audit results.'
        }
    }
}
