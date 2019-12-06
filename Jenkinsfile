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
          withEnv(["HOME=${env.WORKSPACE}"]){
            sh 'pip install -i https://pypi.tuna.tsinghua.edu.cn/simple  -r requirements.txt --user'
          }
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
