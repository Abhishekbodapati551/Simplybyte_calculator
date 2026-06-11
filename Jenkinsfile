pipeline {
    agent { label 'built-in' } // Forces root level clearance
    stages {
        stage('Checkout Code') {
            steps {
                echo 'Successfully pulled code from GitHub...'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t simplybytecalculator .'
            }
        }
        stage('Deploy Live Container') {
            steps {
                sh 'docker rm -f calcu || true'
                sh 'docker run -d -p 3001:5000 --name calcu simplybytecalculator'
            }
        }
    }
}
