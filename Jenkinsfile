pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Verify Files') {
            steps {
                sh '''
                ls -la
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                cp index.html /var/www/html/
                cp style.css /var/www/html/
                cp script.js /var/www/html/
                '''
            }
        }

    }

    post {
        success {
            echo 'Deployment Successful!'
        }
    }
}
