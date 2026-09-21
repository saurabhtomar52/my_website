pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Building Docker image...'

                sh 'sudo docker build -t my-website .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh '''
                    sudo docker stop my-website-container || true
                    sudo docker rm my-website-container || true
                '''
            }
        }

        stage('Run New Container') {
            steps {
                sh '''
                    sudo docker run -d \
                    --name my-website-container \
                    -p 8081:80 \
                    my-website
                '''
            }
        }
    }

    post {
        success {
            echo 'Website deployed successfully using Docker!'
        }

        failure {
            echo 'Docker deployment failed!'
        }
    }
}
