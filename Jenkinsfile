pipeline {
  agent any
  stages {
    stage('Test Pipeline') {
      agent {
        node {
          label 'jenkins-slave'
        }
      }
      steps {
          sh '''
              echo "hello"
              git clone https://gitlab.com/devops1400/dotnet6example.git
              dir('todowebapisample') {
                 sh 'dotnet restore'
                 sh 'dotnet build'
              }
           '''
       }
    }
  }
}
