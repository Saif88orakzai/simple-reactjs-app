pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Saif88orakzai/simple-reactjs-app'
            }
        }
        stage('Dependency Installation') {
            steps {
                bat 'npm install'
            }
        }
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t simple-reactjs-app .'
            }
        }
        stage('Run Docker Image') {
            steps {
                bat 'docker run -d -p 3000:3000 simple-reactjs-app'
            }
        }
        stage('Push Docker Image') {
            steps {
               withcredentials([usernamepassword(credentialsId: 'dockerhub', passwordVariable: 'Ht_70707070', usernameVariable: 'saif88orakzai')]) {
                    bat 'docker login -u $saif88orakzai -p $Ht_70707070'
                    bat 'docker tag simple-reactjs-app $saif88orakzai/simple-reactjs-app'
                    bat 'docker push $saif88orakzai/simple-reactjs-app'
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
