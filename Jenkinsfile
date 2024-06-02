pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/narharigtm/PhpMysql_project.git']])
            }
        }
        stage('build & run'){
            steps{
                sh 'sudo docker-compose up -d'
                sh 'sudo docker ps'
            }
        }
    }
    post {
        success {
            echo 'Pipeline succeeded!'
            sh 'sudo docker-compose down'
        }
        failure {
            echo 'Pipeline failed!'
            sh 'sudo docker-compose down'
        }
    }
}
