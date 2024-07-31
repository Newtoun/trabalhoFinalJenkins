pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/Newtoun/trabalhoFinalJenkins.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t trabalhojenkins:latest .'
                }
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