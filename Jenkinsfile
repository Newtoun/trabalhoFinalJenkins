pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/sarahjl1909/trabalhoFinalJenkins.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t python:3.9-slim trabalhojenkins:latest'
            }

        }

        stage('Run Tests') {
            steps {
                script {
                    docker.image('trabalhojenkins:latest').inside {
                        sh 'python -m unittest discover'
                    }
                }
            }
        }
    }
}