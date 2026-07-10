pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('List Files') {
            steps {
                sh '''
                pwd
                ls -la
                '''
            }
        }

        stage('Verify') {
            steps {
                sh '''
                test -f index.html
                test -f style.css
                test -f script.js

                echo "Website verified."
                '''
            }
        }

    }
}
