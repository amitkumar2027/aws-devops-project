pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo "Cloning Repository..."
                checkout scm
            }
        }

        stage('List Files') {
            steps {
                sh '''
                echo "Current Directory:"
                pwd

                echo "Project Files:"
                ls -la
                '''
            }
        }

        stage('Verify Website Files') {
            steps {
                sh '''
                test -f index.html
                test -f style.css
                test -f script.js

                echo "All required files found."
                '''
            }
        }

    }

    post {

        success {
            echo "Pipeline Executed Successfully."
        }

        failure {
            echo "Pipeline Failed."
        }

    }
}
