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
        echo "install dependenciesi...hiiii.."
        echo "this is just a test"
        sh 'npm install --no-audit'
      }
    }
    stage ('build docker image') {
      steps {
        sh ' docker build -t sanju130/myapp:$GIT_COMMIT .'
      }
    }
    stage ('trivy scan') {
      steps {
        sh 'trivy image sanju130/myapp:$GIT_COMMIT --severity LOW,MEDIUM --exit-code 0 --quiet --format json -o trivy_error.json'
        
      }
    }
    stage ('docker push') {
      steps {
        withDockerRegistry(credentialsId: 'docker-credentials', url: "") {
        sh 'docker push sanju130/myapp:$GIT_COMMIT'
      }
    }
    }
    stage ('deploy in aws') {
      when {
       branch 'main'
      }
      steps {
        script {
        sshagent(['ssh-key']) {
        sh '''
        ssh -o StrictHostKeyChecking=no ec2-user@3.86.30.113 "
        if docker ps -a | grep -q "myapp"; then
        echo "container found..stopping..."
        docker stop "myapp" && docker rm "myapp"
        echo "container stopped and removed"
        fi
        docker run --name myapp \
        -e MONGO_URI=$MONGO_URI \
        -e MONGO_USERNAME=$MONGO_USERNAME \
        -e MONGO_PASSWORD=$MONGO_PASSOWRD \
        -p 3000:3000 -d sanju130/myapp:$GIT_COMMIT
        "
        '''
      }
        }
      }
      
    }
}
  }






      
 
