pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'master', url: 'https://github.com/Syogini1983/flask-hello-world.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-hello-world .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh '''
                    docker rm -f flask-hello-world-container || true
                    docker run -d -p 5000:5000 --name flask-hello-world-container flask-hello-world
                '''
            }
        }
    }

    post {
        success {
            echo 'Application deployed successfully!'
        }
        failure {
            echo 'Deployment failed. Please check the logs.'
        }
    }
}

