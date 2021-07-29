pipeline {
    agent any
    stages {
        stage('test AWS credentials') {
            steps {
                withAWS(credentials: 'AWSCredentials', region: 'us-west-2') {
                    s3Upload acl: 'Private', bucket: 'tayalsakshi-982828900997', file: 'hello.txt'
                    s3Download bucket: 'tayalsakshi-982828900997', file: 'downloadedHello.txt', path: 'hello.txt'
                    sh 'cat downloadedHello.txt'
                }
            }
        }
    }
}
