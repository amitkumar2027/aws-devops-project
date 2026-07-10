pipeline {
    agent any

    environment {
        S3_BUCKET = 'amit-aws-devops-backup'
    }

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
                    echo "Current Working Directory:"
                    pwd

                    echo "Listing Project Files:"
                    ls -la

                    test -f index.html
                    test -f style.css
                    test -f script.js

                    echo "All required files are present."
                '''
            }
        }

        stage('Deploy to Nginx') {
            steps {
                sh '''
                    echo "Deploying website to Nginx..."

                    cp index.html /var/www/html/
                    cp style.css /var/www/html/
                    cp script.js /var/www/html/

                    echo "Website deployed successfully."
                '''
            }
        }

        stage('Verify Deployment') {
            steps {
                sh '''
                    echo "Verifying deployment..."

                    test -f /var/www/html/index.html
                    test -f /var/www/html/style.css
                    test -f /var/www/html/script.js

                    echo "Deployment verification successful."
                '''
            }
        }

    post {
        success {
            echo '==========================================='
            echo 'BUILD SUCCESSFUL'
            echo 'Website deployed and backed up to S3.'
            echo '==========================================='
        }

        failure {
            echo '==========================================='
            echo 'BUILD FAILED'
            echo 'Check Console Output for errors.'
            echo '==========================================='
        }

        always {
            echo 'Pipeline execution completed.'
        }
    }
}
