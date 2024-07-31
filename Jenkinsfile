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
                script {
                    docker.build('trabalhojenkins:latest')
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