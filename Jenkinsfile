pipeline {
  agent any
  tools {
    nodejs 'nodeJS2390'
  }
  stages {
    stage ("npm dependencies install") {
      steps {
        echo "install dependenciesi..."
        echo "this is just a test"
        sh 'npm install --no-audit'
      }
    }
   
      stage ("unit testing") {
       steps {
         echo "do unit test"
         sh 'npm test'
       }
        
      }
}
  }


      
 
