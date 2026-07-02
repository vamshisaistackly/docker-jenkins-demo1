pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t website:v1 .'
            }
        }

        stage('Remove Old Container') {
            steps {
                bat 'docker stop website || exit 0'
                bat 'docker rm website || exit 0'
            }
        }

        stage('Deploy') {
            steps {
                bat 'docker run -d -p 80:80 --name website website:v1'
            }
        }
    }
}