pipeline {
  agent { 
      docker { 
          image 'python:3.7.2' 
          label 'Slave-01'
      } 
  }
  stages {
    stage('build') {
      steps {
        sh 'pip install -r requirements.txt --user'
      }
    }
    stage('test') {
      steps {
        sh 'python test.py'
      }
      post {
        always {
          junit 'test-reports/*.xml'
        }
      }    
    }
  }
}
