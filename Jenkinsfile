pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/wookim3593/jen', branch: 'main'
      }
    }
    stage('docker build and push') {
      steps {
        sh '''
        sudo docker build -t wookim3593/myweb:1.2 .
        sudo docker push wookim3593/myweb:1.2
        '''
      }
    }
    stage('deploy k8s') {
      steps {
        sh '''
        sudo kubectl apply -f deploy.yml
        '''
      }
    }
  }
}
