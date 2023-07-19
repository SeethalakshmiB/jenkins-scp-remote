pipeline {
    agent any
    
    
    stages {
        stage('Git Clone'){
            steps {
                git credentialsId: 'github-token', url: 'https://github.com/SeethalakshmiB/docker-micro-service-example'
            }
        }
        
        stage('SCP copy') {
            steps {
                sshagent(['scp-ec2-creds']) {
                    sh '''
                    ls
                    scp -r python-flask-1t ec2-user@<ec2_ip>:/home/ec2-user/
                    '''
                }
            }
        }
    }
}