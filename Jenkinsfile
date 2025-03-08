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
         junit allowEmptyResults: true, skipPublishingChecks: true, testResults: 'test-results.xml'
       }
        
      }
    stage ("code coverage") {
     steps {
       echo "code coverage check "
       withCredentials([usernamePassword(credentialsId: 'mongo-db-credentials', passwordVariable: 'MONGO_PASSWORD', usernameVariable: 'MONGO_USERNAME')]) {
       catchError(buildResult: 'SUCCESS', message: 'opps!! will be taken care later', stageResult: 'UNSTABLE') { 
       sh 'npm run coverage'
     }
     }
       publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, icon: '', keepAll: false, reportDir: 'coverage/lcov-report', reportFiles: 'index.html', reportName: 'code coverage HTML Report', reportTitles: '', useWrapperFileDirectly: true])
    }
}
  }
}



      
 
