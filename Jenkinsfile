pipeline {
  agent any
  tools {
    nodejs 'nodeJS2390'
  }
  stages{
    stage("deployment_to_dev ") {
      when {
        expression { return env.BRANCH_NAME == 'feature_1' }
    }
    steps {
        echo 'Deploying to developemnt...'
    }

      
    }
stage("deployment_to_PROD ") {
      when {
        expression { return env.BRANCH_NAME == 'main' }
    }
    steps {
        echo 'Deploying to production...'
    }

      
    }
    
  }
}
