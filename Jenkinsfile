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
              cd dotnet6example/todowebapisample
              sh 'dotnet restore'
              sh 'dotnet build'
           '''
       }
    }
  }
}
