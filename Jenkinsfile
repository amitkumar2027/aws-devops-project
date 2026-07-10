pipeline {
    agent any

    stages {

        stage('Checkout Source') {
            steps {
                echo 'Checking out source code...'
                checkout scm
            }
        }

        stage('Verify Project Files') {
            steps {
                sh '''
                    echo "Current Directory:"
                    pwd

                    echo "Project Files:"
                    ls -la

                    test -f index.html
                    test -f style.css
                    test -f script.js

                    echo "All website files found."
                '''
            }
        }

        stage('Deploy to Nginx') {
            steps {
                sh '''
                    echo "Deploying website..."

                    cp index.html /var/www/html/
                    cp style.css /var/www/html/
                    cp script.js /var/www/html/

                    echo "Deployment Successful!"
                '''
            }
        }

        stage('Verify Deployment') {
            steps {
                sh '''
                    echo "Checking deployed files..."

                    ls -la /var/www/html/

                    test -f /var/www/html/index.html
                    test -f /var/www/html/style.css
                    test -f /var/www/html/script.js

                    echo "Deployment Verified Successfully!"
                '''
            }
        }
    }

    post {
        success {
            echo 'BUILD SUCCESSFUL'
        }

        failure {
            echo 'BUILD FAILED'
        }

        always {
            echo 'Pipeline Finished'
        }
    }
}
