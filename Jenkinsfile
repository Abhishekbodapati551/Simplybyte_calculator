pipeline {
    agent any
    stages {
        stage('Checkout Code') {
            steps {
                echo 'Successfully pulled code from GitHub...'
            }
        }
        stage('Build Docker Image') {
            steps {
                // Using the exact lowercase image tag found in your 'docker images' command
                sh 'docker build -t simplybytecalculator .'
            }
        }
        stage('Deploy Live Container') {
            steps {
                // Safely replaces the 'calcu' container on port 3001
                sh 'docker rm -f calcu || true'
                sh 'docker run -d -p 3001:5000 --name calcu simplybytecalculator'
            }
        }
    }
}
