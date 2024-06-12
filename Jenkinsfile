pipeline {
    agent any

    stages { 
        stage('Docker Build') {
            steps {
                script {
                    bat 'docker build -t server:latest ./server'
                    bat 'docker build -t client:latest ./client'                
                }
            }
        }
       
        stage('Docker Push client') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'docker-repo'){
                        bat 'docker tag client:latest bahizak01/client'
                        bat 'docker push bahizak01/client'
                    }
                }
            }
        }
       
        stage ('Docker Push server') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'docker-repo') {
                        bat 'docker tag server:latest bahizak01/server'
                        bat 'docker push bahizak01/server'
                    }
                }
            }
        }
    }
}