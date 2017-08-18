pipeline {
  agent {
    docker {
      image 'ctsrd/cheri-sdk-cheri256'
    }
    
  }
  stages {
    stage('Example') {
      steps {
        parallel(
          "Example": {
            echo 'Hello World'
            
          },
          "branch 2": {
            sh '''echo branch 2

'''
            
          }
        )
      }
    }
    stage('stage2') {
      steps {
        ws(dir: 'worksapce2') {
          ansiColor(colorMapName: 'xterm') {
            script {
              echo "hi"
            }
            
            sh 'pwd'
          }
          
        }
        
      }
    }
  }
  post {
    always {
      echo 'I will always say Hello again!'
      
    }
    
  }
}
