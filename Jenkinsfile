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
                // This removes our new automated container name if it exists
                sh 'docker rm -f calcu-jenkins || true'
                // This runs it cleanly on port 3005 under the name calcu-jenkins
                sh 'docker run -d -p 3005:5000 --name calcu-jenkins simplybytecalculator'
            }
        }

    }
}
