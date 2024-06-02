pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/narharigtm/PhpMysql_project.git']])
            }
        }
        stage('build'){
            steps{
                sh 'sudo docker-compose --build'
                sh 'sudo docker images'
            }
        }
        stage('push'){
            steps{
                withDockerRegistry(credentialsId: 'narharigtm', url: 'https://github.com/narharigtm/PhpMysql_project.git')               
                sh 'sudo docker tag phpmysqlimg narhari/phpmysqlimg:V1'
                sh 'sudo docker push narhari/phpmysqlimg:V1'
            }
        }
         stage('run'){
            steps{
                sh 'sudo docker-compose up -d'
                sh 'sudo docker ps'
            }
        }   
    
    post {
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
    }
        
}
    
        
        
   
