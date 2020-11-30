pipeline {
     agent any
     stages {
         stage('Build') {
             steps {
                 sh 'pip install boto'
                 sh 'pip install tox'
             }
         }
         stage('Lint HTML') {
              steps {
                  sh 'tidy -q -e *.html'
              }
         }
         stage('Upload to AWS') {
              steps {
                  withAWS(region:'us-west-2',credentials:'devuser') {
                  sh 'echo "Uploading content with AWS creds"'
                      s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'jenkinspipelinectb/Main')
                  }
              }
         }
     }
}
