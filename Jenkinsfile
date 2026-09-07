pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Building website...'
                sh 'ls -la'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    sudo rm -rf /var/www/html/*
                    sudo cp -r ./* /var/www/html/
                '''
            }
        }

        stage('Restart Apache') {
            steps {
                sh 'sudo systemctl reload apache2'
            }
        }
    }

    post {
        success {
            echo 'Website deployed successfully!'
        }

        failure {
            echo 'Deployment failed!'
        }
    }
}
