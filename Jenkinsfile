pipeline {
     agent any
     stages {
         stage('Build') {
             steps {
                 sh 'echo "Hello World"'
                 sh '''
                 echo "Multiline shell steps works too"
                 ls -lah'''
             }
         }
         stage('Lint HTML') {
             steps {
                  sh 'ls'
                 sh  'tidy -q -e index.html'
             }
         }      
         stage('Upload to AWS') {
              steps {
                  withAWS(region:'us-west-2',credentials:'aws-static') {
                    s3Upload(pathStyleAccessEnabled:true, payloadSigningEnabled: true, file:'index.html', bucket:'jenkinsgc')
                  }
                }
              }
            }
          }
