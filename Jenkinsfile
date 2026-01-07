pipeline {
    agent any

    stages {
        stage('Clone Code') {
            steps {
                echo 'Cloning source code from GitHub'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t jenkins-nginx .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker rm -f web || true
                docker run -d -p 80:80 --name web jenkins-nginx
                '''
            }
        }
    }
}
