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
    stage ("parallel check") {
      parallel {
   stage ("npm audits") {
     steps {
       echo "performing audits.."
       sh 'npm audit --audit-level=critical'  
}


}
    stage ("owasp check") {
    steps {
      dependencyCheck additionalArguments: '''--scan /\'./ \\\'
--format / \'./ \\\'
--out `\\All `\\
--prettyPrint''', odcInstallation: 'Owasp1210'
  }
  }
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


      
 
