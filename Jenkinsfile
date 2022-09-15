pipeline {
    agent any

    stages {
        stage('ci') {
            steps {
                sh 'zip -r html-helloworld-$BUILD_NUMBER.zip *'
                sh 'aws s3 cp html-helloworld-$BUILD_NUMBER.zip s3://artifactory-cicd-sainath/'
            }
        }
         stage('cd') {
            steps {
                sh 'rm -fr *'
                sh 'aws s3 cp s3://artifactory-cicd-sainath/html-helloworld-$BUILD_NUMBER.zip .'
                sh 'unzip html-helloworld-$BUILD_NUMBER.zip'
                sh 'scp index.html root@172.31.33.94:/var/www/html/'
            }
        }
    }
}
