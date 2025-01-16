pipeline {
    agent any

    stages {
        stage('Git checkout') {
            steps {
                echo 'checking out the git repo'
                git 'https://github.com/Aastha22j02/HealthCare-Medicure-DevOps-Project-aastha.git'
                
                
            }
        }
        stage('pkg the code aastha') {
            steps {
                echo 'packaing the code '
                sh 'mvn clean package'
            }
        }
        stage('Building the docker img') {
            steps {
                echo 'Docker imges build '
                sh 'docker build -t aasthagupta02/healthcare-aastha:1 .'
            }
        }
        stage('docker login aastha') {
            steps {
                withCredentials([string(credentialsId: 'dockerhubpass', variable: 'dockerhubpass')]) {
                sh 'docker login -u aasthagupta02 -p ${dockerhubpass}'
                sh 'docker push aasthagupta02/healthcare-aastha:1'
                }
            }
        }
        stage('port expose'){
            steps{
                sh 'docker run -dt -p 8082:8082 --name c00 aasthagupta02/healthcare-aastha:1'
            }
        }   
        stage('deploy on production'){
            steps{
                sh 'sudo kubectl apply -f deployment.yaml'
                sh 'sudo kubectl get all'
            }
        }
    }
}
