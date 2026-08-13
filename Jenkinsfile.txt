pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t devops-cicd-pipeline:1.0 .'
            }
        }

        stage('Docker Push') {
            steps {
                bat 'docker push shravani43/devops-cicd-pipeline:1.0'
            }
        }
    }
}