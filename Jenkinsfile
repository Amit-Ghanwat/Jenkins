pipeline {
    agent any
    stages{
        stage('pull') {
            steps{
            git branch: 'main', url: 'https://github.com/Amit-Ghanwat/Resume.git'
            }
        }
    
        stage('build') {
            steps{
                script{
                sh '''docker build -t first-try3:v4 .
                docker images
                docker image tag first-try3:v4 amitghanvat/first-try3:v4'''
                }
            }
        }
    
        stage('Push'){
            steps{
                script{
                    withCredentials([string(credentialsId: 'name', variable: 'dockerpass')]) {
                    sh 'docker login -u amitghanvat -p ${dockerpass}'    
                    }

                    sh 'docker image push amitghanvat/first-try3:v4'
                }
            }
        }
    }
}