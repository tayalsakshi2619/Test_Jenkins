pipeline {
    agent any
    stages {
        stage('test AWS credentials') {
            steps {
                withAWS(credentials: 'AWSCredentials', region: 'us-west-2') {
                    sh 'echo "hello Jenkins">abc1.txt'
                    s3Upload acl: 'Private', bucket: 'tayalsakshi-982828900997', file: 'abc1.txt'
                    s3Download bucket: 'tayalsakshi-982828900997', file: 'downloadedabc1.txt', path: 'abc1.txt'
                    sh 'cat downloadedabc1.txt'
                }
            }
        }
          stage('send slack notification')
        { 
            steps{
                slackSend color: "good", message: "Message from Jenkins Pipeline"
            }
        }
    }
}
