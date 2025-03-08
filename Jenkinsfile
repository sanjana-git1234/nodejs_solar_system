pipeline {
  agent any
  tools {
    nodejs 'nodeJS2390'
  }
  environment {
  MONGO_URI = "mongodb+srv://supercluster.d83jj.mongodb.net/superData"
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
         withCredentials([usernamePassword(credentialsId: 'mongo-db-credentials', passwordVariable: 'MONGO_PASSWORD', usernameVariable: 'MONGO_USERNAME')]) {
         sh 'npm test'
       }
       }
        
      }
}
  }


      
 
