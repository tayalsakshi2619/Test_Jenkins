pipeline {
    agent any
    stages {
        stage('test AWS credentials') {
            steps {
                withAWS(credentials: 'AWSCredentials', region: 'us-west-2') {
                    sh 'echo "hello Jenkins">abc.txt'
                    s3Upload acl: 'Private', bucket: 'tayalsakshi-982828900997', file: 'abc.txt'
                    s3Download bucket: 'tayalsakshi-982828900997', file: 'downloadedabc.txt', path: 'abc.txt'
                    sh 'cat downloadedabc.txt'
                }
            }
        }
    }
}
