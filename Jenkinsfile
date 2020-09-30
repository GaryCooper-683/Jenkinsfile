pipeline {
     agent any
  stages {
    stage("Lint HTML") {
      steps {
        sh 'tidy -q -e *.html'  
      }
    }
    stage('Upload to AWS') {
      steps {
        withAWS(region:'us-west-2',credentials:'aws-static') {
          sh 'echo "Uploading content with AWS creds"'
          s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'udacityjenkins')
        }
      }
    }

  }
}
 stage("Ensure content is up"){
            steps{
                retry(3){
                sh '''
                        if curl --silent --head --fail "http://udacityjenkins.s3-website.us-west-2.amazonaws.com/"; then \
                            echo "The content is up ... "; \
                            exit 0; \
                        else \
                            echo "This URL Not Exist !!"; \
                            exit 1; \
                        fi 
                '''
            }}
        }
    }
}
