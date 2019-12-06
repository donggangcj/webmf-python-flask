pipeline {
  agent { 
      label 'Slave-01'
  }
  stages {
    stage('test') {
      agent { 
        docker { 
            image 'python:3.7.2' 
        } 
      }
      steps {
          withEnv(["HOME=${env.WORKSPACE}"]){
            sh 'pip install -i https://pypi.tuna.tsinghua.edu.cn/simple  -r requirements.txt --user'
            sh 'python test.py'
          }
      }
      post {
        always {
          junit 'test-reports/*.xml'
        }
      }    
    }
    stage('build') {
      steps{
        sh  'docker build -t flask-demo .'
      }
    }
  }
}
