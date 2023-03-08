pipeline {
    agent {
        docker {image 'mcr.microsoft.com/dotnet/sdk:5.0' }
    }
    stages {

        stage('Clone repository') {
            steps {
                git clone https://gitlab.com/devops1400/dotnet6example.git
            }
        }
        stage('Build') {
            steps {
                dir('dotnet6example/todowebapisample') {
                    sh 'docker build -t todowebapisample:latest f Dockerfile -t .'
                }
            }
        }
    }
}
