pipeline {
  agent any
  stages {
    stage('test pipeline') {
      agent {
        node {
          label 'jenkins-slave'
        }
      }
      steps {
        sh '''
          echo "hello"
          git clone https: //github.com/marcel-dempers/docker-development-youtube-series.git
          cd. / docker - development - youtube - series / golang
          docker build. - t test 
        '''
      }
    }
  }
}
