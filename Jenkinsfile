pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/narharigtm/PhpMysql_project.git']])
            }
        }
        stage('Build') {
            steps {
                sh 'sudo docker-compose build'
                sh 'sudo docker images'
            }
        }

        stage('Run') {
            steps {
                sh 'sudo docker-compose up -d'
                sh 'sudo docker ps'
            }
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
}
