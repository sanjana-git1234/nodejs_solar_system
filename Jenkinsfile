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
   
      stage ("unit testing") {
       steps {
         echo "do unit test"
         sh 'colon separated - $MONGO_DB_CREDS'
         sh 'echo username - $MONGO_DB_CREDS_USR'
         sh 'echo password - $MONGO_DB_CREDS_PSW'
         sh 'npm test'
         
         junit allowEmptyResults: true, skipPublishingChecks: true, testResults: 'test-results.xml'
       }
      }
    stage ("code coverage") {
     steps {
       echo "code coverage check "
      
       catchError(buildResult: 'SUCCESS', message: 'opps!! will be taken care later', stageResult: 'UNSTABLE') { 
       sh 'npm run coverage'
     }
     
       publishHTML([allowMissing: true, alwaysLinkToLastBuild: true, icon: '', keepAll: true, reportDir: 'coverage/lcov-report', reportFiles: 'index.html', reportName: 'code coverage HTML Report', reportTitles: '', useWrapperFileDirectly: true])
       
    }
      
}
  }
}



      
 
