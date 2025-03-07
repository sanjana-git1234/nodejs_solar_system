pipeline {
  agent any
  tools {
    nodejs 'nodeJS2390'
  }
  stages{
    stage("deployment") {
      when {
        expression { return env.BRANCH_NAME == 'main' }
    }
    steps {
        echo 'Deploying to production...'
    }

      
    }
  }
}
