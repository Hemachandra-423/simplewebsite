pipeline {
    agent any
    stages {
        stage('Lint HTML') {
            steps {
                sh 'tidy -q -e index.html'
            }
        }
        stage('Upload to AWS') {
            steps {
		withAWS(region:'us-east-2',credentials:'aws-static'){   
		    sh 'echo "Hello World with AWS creds"'
		    s3upload(pathStyleAccessEnabled: true, payloadSignEnabled: true, file: "index.html", bucket:'konihe-aws-pipeline')
	        }
            }
        }
    }
}
