pipeline {
  agent any
  tools {
    nodejs 'nodeJS2390'
  }
  environment {
  MONGO_URI = "mongodb+srv://supercluster.d83jj.mongodb.net/superData"
  //MONGO_DB_CREDS = credentials ('mongo-db-credentials')
  MONGO_USERNAME = credentials ('mongo_username')
  MONGO_PASSWORD = credentials ('mongo_password')
}

  stages {
    stage ("npm dependencies install") {
      steps {
        echo "install dependenciesi...hiiii..."
        echo "this is just a test"
        sh 'npm install --no-audit'
      }
    }
    stage ('build docker image') {
      steps {
        sh ' docker build -t myapp:latest:$GIT_COMMIT .'
      }
    }
      
}
  }






      
 
