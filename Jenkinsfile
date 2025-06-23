pipeline {
    agent any
    environment {
        REMOTE_USER = 'apache'
        REMOTE_HOST = '10.121.5.205'
        SSH_KEY_ID = 'apache-ssh-key'
        WEB_ROOT = '/var/www/html/webroot/ROOT' // Adjust if different
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Deploy HTML') {
            steps {
                sshagent(credentials: [env.SSH_KEY_ID]) {
                    sh """
                    scp -o StrictHostKeyChecking=no index.html ${REMOTE_USER}@${REMOTE_HOST}:${WEB_ROOT}/index.html
                    """
                }
            }
        }
    }
}

