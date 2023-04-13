pipeline {
    agent any
    
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/20it047/BookStore.git'
            }
        }
        
        stage('Build and Test') {
            steps {
                sh 'mvn clean install' 
            }
        }
        
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t hirenhk39/bookstore .'
            }
        }
        
        stage('Push Docker Image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-credentials-id', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                    sh 'docker login -u hirenhk39 -p kenilKK39_@'
                    sh 'docker push hirenhk39/bookstore:V1'
                }
            }
        }
    }
}
