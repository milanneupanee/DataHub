pipeline {
    agent any
    environment {
        REMOTE_USER = 'apache'
        REMOTE_HOST = '10.121.7.133'    // Apache server IP or hostname
        SSH_CREDENTIALS_ID = 'apache-ssh-key'
        REMOTE_WEB_ROOT = '/var/www/html/webroot/ROOT' // adjust as needed
    }
    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }
        stage('Deploy to Apache Server') {
            steps {
                sshagent(credentials: [env.SSH_CREDENTIALS_ID]) {
                    sh '''
                        scp -o StrictHostKeyChecking=no index.html ${REMOTE_USER}@${REMOTE_HOST}:${REMOTE_WEB_ROOT}/index.html
                    '''
                }
            }
        }
    }
}
