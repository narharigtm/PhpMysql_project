pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/narharigtm/PhpMysql_project.git']])
            }
        }
        stage('compose'){
            steps{
                sh 'sudo docker-compose up -d --build'
                sh 'sudo docker ps'
            }
        }
        stage('push'){
            steps{
                withDockerRegistry(credentialsId: 'narharigtm', url: 'https://github.com/narharigtm/PhpMysql_project.git')               
                sh 'sudo docker image tag phpmysqlimg narhari/phpmysqlimg:V1'
                sh 'sudo docker push narhari/phpmysqlimg:V1'
            }
        }

    }
