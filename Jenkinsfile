pipeline{
    agent any
    stages{
        stage('checkout the code from github'){
            steps{
                 git url: 'https://github.com/Aastha22j02/Banking-financeMe-DevOps-aastha/'
                 echo 'github url checkout'
            }
        }
        stage('codecompile with aastha'){
            steps{
                echo 'starting compiling'
                sh 'mvn compile'
            }
        }
        stage('codetesting with aastha'){
            steps{
                sh 'mvn test'
            }
        }
        stage('qa with aastha'){
            steps{
                sh 'mvn checkstyle:checkstyle'
            }
        }
        stage('package with aastha'){
            steps{
                sh 'mvn package'
            }
        }
        stage('run dockerfile'){
          steps{
               sh 'docker build -t myimg .'
           }
         }
        stage('port expose'){
            steps{
                sh 'docker run -dt -p 8091:8091 --name c000 myimg'
            }
        }   
    }
}
